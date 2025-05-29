```
read_mdsio(pth::String,fil::String)
```

Read a set of `MITgcm` MDSIO-type files (".data" binary + ".meta" text pair), combine, and return as an Array. Unlike `read_mdsio(fil::String)` where `fil` is one complete file name, this method will search within `pth` for files that start with `fil`.

```
p="./hs94.cs-32x32x5/run/"
x=read_mdsio(p,"surfDiag.0000000020")
y=read_mdsio(p,"pickup.ckptA")
z=read_mdsio(p,"T.0000000000")
```
