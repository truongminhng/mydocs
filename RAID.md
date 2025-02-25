# RAID - Redundant Array of Independent Disks

Raid a set of **physical disks** viewed by the OS as one **logical disk**. RAID is used for its data REDUNDANCY and RECOVERY on the disks. There numbers of RAID, but RAID 0,1,5 and 10 are the most common ones.

### RAID 0

Data is **striped** across the disks.

**pros:** requests to/from the disks can be done in **parallel** --> faster speed. <br>
**cons:** If one disk is error, the entire data is lost --> Zero redundancy

Min disk: 1 <br>
Capacity: Σ all disks <br>
Speed: Σ all disks <br>
Min disk to fail: 0 disk


### RAID 1

Data is **mirrored**

**pros:** if one disk is error, there's still the other for backup --> redundancy <br>
**cons:** Requests can't be done in parallel --> Slower speed

Min disk: 2 disks <br>
Capacity: 1 disk <br>
Speed: Σ all disks <br>
Mininum disk to fail: 1

### RAID 5 
Data is **striped** across the disks with a parity information of another disk in each disk. Data can be rebuilt with the parity.

**pros:** Good speed (striped), redundancy (parity) <br>
**cons:** complex controller design, parity calculation can reduce speed.

Min disk: 3 disks <br>
Capacity: n-1 disks <br>
Speed: n-1 disks <br>
Mininum disk to fail: 2

### RAID 1+0

Combine two RAIDs 1 and 0 together: stripe(mirror(Disk1, Disk2), mirror(Disk3, Disk 4))

stripe = RAID 0; mirror = RAID 1

**pros:** SPEED & REDUNDANCY <br>
**cons:** costly

Min disk: 4 disks <br>
Capacity: Σ RAID 1 branches <br>
Speed: Σ RAID 1 branches <br>
Mininum disk to fail: 1 branch of RAID 1

### Summary

| RAID | Min Disks | Capacity (4TB Drives) | Speed      | Fault Tolerance | Scenario                  | Cost (Approx.) |
|------|-----------|-----------------------|------------|-----------------|---------------------------|----------------|
| 0    | 2         | 8TB                   | Very Fast  | None            | Video editing            | $200–$300      |
| 1    | 2         | 4TB                   | Decent     | 1 disk          | Small office server      | $200–$300      |
| 5    | 3         | 8TB                   | Good       | 1 disk          | Business NAS             | $500–$600      |
| 10   | 4         | 8TB                   | Excellent  | 1 per pair      | Database server          | $600–$800      |


