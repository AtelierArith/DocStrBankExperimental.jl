```
read_newick(in_file::String,
            fossil ::Bool;
            ix     ::OrdinalRange{Int64,Int64} = 0:0,
            ne     ::Float64                   = accer)
```

Reads a newick tree into `sTf` from `in_file` at lines `ix`.
