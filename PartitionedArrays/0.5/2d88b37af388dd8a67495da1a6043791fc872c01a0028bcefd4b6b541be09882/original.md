```
ids_snd, ids_rcv = assembly_local_indices(index_partition)
```

Return the local ids to be sent and received   in the assembly of distributed vectors defined on the index partition `index_partition`.

Local values corresponding to the local indices in `ids_snd[i]` (respectively `ids_rcv[i]`) are sent to part `neigs_snd[i]` (respectively `neigs_rcv[i]`), where `neigs_snd, neigs_rcv = assembly_neighbors(index_partition)`.
