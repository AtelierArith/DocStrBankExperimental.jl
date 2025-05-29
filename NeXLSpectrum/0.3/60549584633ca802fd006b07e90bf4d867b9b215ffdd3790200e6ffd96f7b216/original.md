```
filterreference(
    filt::TopHatFilter{T},
    spec::Spectrum,
    elm::Element,
    allElms::[AbstractSet{Element}|Material]
    props::Dict{Symbol,<:Any} = Dict{Symbol,Any}(),
    withEsc::Bool = false,
)
filterreferences(
    filt::TopHatFilter,
    refs::Tuple{Spectrum,Element,Material}...;
    props::Dict{Symbol,<:Any} = Dict{Symbol,Any}(),
    withEsc::Bool = false,
)
```
