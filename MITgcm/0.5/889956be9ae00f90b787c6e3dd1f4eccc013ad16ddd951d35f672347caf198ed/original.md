```
read_meta(metafile)
```

Read a `MITgcm` metadata file, parse it, and return as a NamedTuple

```
p="./hs94.cs-32x32x5/run/"
meta=read_meta(p*"surfDiag.0000000020.002.001.meta")
pairs(meta)
meta.dimList
```
