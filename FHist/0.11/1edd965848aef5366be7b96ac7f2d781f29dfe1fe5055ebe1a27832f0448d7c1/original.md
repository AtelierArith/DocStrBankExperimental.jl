# To make an **empty** histogram

use the all-keyword-arguments constructor:

```julia
FHist.Hist2D(;
    counttype=Float64,
    binedges::E
    bincounts = zeros(counttype, length.(_to_tuple(binedges)) .- 1),
    sumw2 = zero(bincounts),
    nentries = 0
    overflow::Bool = false
) where {E<:NTuple{2,Any}}
```

!!! note
    Everything other than `binedges` are optional (infered from `binedges`).


# To make an histogram given data (and weights etc.)

use the a positional argument for data and keyword-arguments for the rest:

```julia
FHist.Hist2D(array::E;
    counttype=Float64,
    binedges=nothing,
    weights=nothing,
    nbins=nothing,
    overflow=false)
) where {E<:NTuple{2,Any}}
```

!!! note
    Everything other than data (`array`) is optional (infered from data).

