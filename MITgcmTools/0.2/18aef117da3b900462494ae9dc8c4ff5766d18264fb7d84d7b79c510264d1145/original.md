```
read_meta(pth::String,fil::String)
```

Read a `MITgcm` metadata files, parse them, and return as an array of NamedTuple

```
p="./hs94.cs-32x32x5/run/"
meta=read_meta(p,"surfDiag.0000000020")
pairs(meta[end])
[meta[i].dimList for i in 1:length(meta)]
```
