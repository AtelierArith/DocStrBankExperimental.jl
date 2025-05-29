```
psi = randMPS(physindvec,Ns[,oc=1,m=1])
```

Generates random MPS with data type Float64, physical index size vector `physindvec` (repeating over `Ns` sites, `physindvec` can be smaller than `Ns` where the inputs will repeat), orthogonality center `oc`, and bond dimension `m`.
