```
box1([T=Float64], size::NTuple{N, Int};
    offset=CtrFT,
    dims=ntuple(+, N),
    scale=ScaUnit)
```

See `rr2` for a description of all options.

Returns an IndexFunArray with being one if any lateral distance of a pixel to the center is smaller than or equal to 1.0. This function is used more as a helper function for the function `box` which warrants the box length to agree to a specified box size. This function calculates on a pixel by pixel basis, which means that you have to apply a subpixel offset, if you want boxes with even-sized pixel width. The size of the box can be regulated by the `scale` parameter. See `box` for a more convenient version.
