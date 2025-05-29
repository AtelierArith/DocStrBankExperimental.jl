```
read_mdsio(fil::String)
```

Read a single `MITgcm` MDSIO-type file (".data" binary + ".meta" text pair), and return as an Array

```
p="./hs94.cs-32x32x5/run/"
x=read_mdsio(p*"surfDiag.0000000020.002.001.data")
y=read_mdsio(p*"pickup.ckptA.002.001.data")
z=read_mdsio(p*"T.0000000000.002.001.data")
```
