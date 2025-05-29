```
disc1([T=Float64], size::NTuple{N, Int};
    offset=CtrFT,
    dims=ntuple(+, N),
    scale=ScaUnit)
```

See `rr2` for a description of all options.

Returns an IndexFunArray with the radius to the center is smaller than or equal to 1.0. This function is used more as a helper function for the function `disc`. The radius of the disc can be regulated by the `scale` parameter. See `disc` for a more convenient version.
