```
uv(spec::Spectrum, chs::AbstractRange{<:Integer}=eachindex(spec))::Vector{UncertainValue}
```

Converts the count's data in a spectrum into an Vector{UncertainValue} assuming count statistics can be approximated by C ± √C. 
