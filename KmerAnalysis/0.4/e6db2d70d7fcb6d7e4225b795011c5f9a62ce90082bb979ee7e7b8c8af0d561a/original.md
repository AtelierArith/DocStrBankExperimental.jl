```
add_count!(mc::IndexedCounts{M}, name::Symbol, reads::ReadDatastore) where {M}
```

Count the k-mers in a ReadDatastore and add them to the IndexedCounts{M}.

Currently IndexedCounts use a serial and in-memory counting method, as 

!!! note
    Only the k-mers in the IndexedCounts' index shall be counted from the reads.

