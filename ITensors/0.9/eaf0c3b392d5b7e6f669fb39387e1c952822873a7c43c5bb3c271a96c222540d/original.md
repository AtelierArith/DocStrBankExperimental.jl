```
random_itensor([::Type{ElT} = Float64, ][flux::QN = QN(), ]inds)
random_itensor([::Type{ElT} = Float64, ][flux::QN = QN(), ]inds::Index...)
```

Construct an ITensor with `NDTensors.BlockSparse` storage filled with random elements of type `ElT` where the nonzero blocks are determined by `flux`.

If `ElT` is not specified it defaults to `Float64`. If the flux is not specified it defaults to `QN()`.
