```
qrm_init(ncpu, ngpu)
```

This routine initializes qr_mumps and should be called prior to any other qr_mumps routine. This function is automatically called if you use qr_mumps precompiled with Yggdrasil.

```
qrm_init()
```

`ncpu` and `ngpu` are optional arguments and their default value are, respectively, `1` and `0`.

#### Input Arguments :

  * `ncpu`: number of working threads on CPU.
  * `ngpu`: number of working threads on GPU.
