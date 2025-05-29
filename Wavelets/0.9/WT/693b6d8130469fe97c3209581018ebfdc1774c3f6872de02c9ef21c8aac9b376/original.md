```
CFW(wave::WC, scalingFactor::S=8.0, averagingType::Symbol=:Father,
    boundary::T=WT.DEFAULT_BOUNDARY, averagingLength::Int =
    floor(Int,2*scalingFactor), frameBound::Float64=1.0,
    normalization::Float=Inf) where {WC<:WT.WaveletClass,
    T<:WT.WaveletBoundary, S<:Real}
```

The constructor for the CFW struct. w is a type of continuous wavelet, scalingFactor is the number of wavelets between the octaves $2^J$ and $2^{J+1}$ (defaults to 8, which is most appropriate for music and other audio). As this leads to excessively many high scale wavelets, `decreasing` gives the amount that scalingFactor decreases per octave. The default boundary condition is `periodic`, which is implemented by appending a flipped version of the vector at the end (to eliminate edge discontinuities). Alternatives are `ZPBoundary`, which pads with enough zeros to get to the nearest power of 2 (here the results returned by caveats are relevant, see Torrence and Compo '97), and `NullBoundary`, which assumes the data is inherently periodic.

`averagingLength` and `averagingType` determine how wide scale information is accounted for. `averagingLength` gives the number of wavelet octaves that are covered by the averaging, while averaging type determines whether it is a window `Dirac` or a wavelet `Father`. `frameBound` gives the total norm of the whole collection, corresponding to the upper frame bound. `normalization` refers to which p-norm is preserved as the scale changes. `normalization==2` is the default scaling, while `normalization==Inf` gives all the same maximum value, thus acting more like windows.
