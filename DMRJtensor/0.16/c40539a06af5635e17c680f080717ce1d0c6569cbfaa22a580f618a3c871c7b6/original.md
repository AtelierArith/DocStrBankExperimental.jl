```
psi = randMPS(Qlabel,Ns[,m=2,type=Float64,flux=...])
```

generates a random MPS from `qnum`s on a given site stored in an array of vectors `Qlabel` for `Ns` sites (will repeat if `Ns` is longer than array); bond dimension `m`; `type` for the element types; and overall `flux` (default zero of type given in `Qlabel`)
