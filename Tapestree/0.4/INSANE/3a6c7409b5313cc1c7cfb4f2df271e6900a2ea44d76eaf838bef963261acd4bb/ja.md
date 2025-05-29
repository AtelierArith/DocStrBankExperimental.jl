```
read_newick(in_file::String,
            fossil ::Bool;
            ix     ::OrdinalRange{Int64,Int64} = 0:0,
            ne     ::Float64                   = accer)
```

`in_file`から行`ix`で`sTf`にnewickツリーを読み込みます。
