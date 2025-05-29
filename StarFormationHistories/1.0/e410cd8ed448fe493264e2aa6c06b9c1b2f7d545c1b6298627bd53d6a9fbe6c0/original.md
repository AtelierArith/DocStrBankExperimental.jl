```
result::StatsBase.Histogram =
    partial_cmd(m_ini::AbstractVector{<:Number},
                colors::AbstractVector{<:Number},
                mags::AbstractVector{<:Number},
                imf;
                dmod::Number=0,
                normalize_value::Number=1,
                mean_mass::Number=mean(imf),
                edges=nothing,
                xlim=extrema(colors),
                ylim=extrema(mags),
                nbins=nothing,
                xwidth=nothing,
                ywidth=nothing)
```

Creates an error-free Hess diagram for stars from an isochrone with x-axis photometric `colors`, y-axis photometric magnitudes `mags`, and initial masses `m_ini`. Because this is not smoothed by photometric errors, it is not generally useful but is provided for comparative checks. Most arguments are as in [`bin_cmd`](@ref). The only unique keyword arguments are `normalize_value::Number` which is a multiplicative factor giving the effective stellar mass you want in the Hess diagram, and `mean_mass::Number` which is the mean stellar mass implied by the provided initial mass function `imf`. 
