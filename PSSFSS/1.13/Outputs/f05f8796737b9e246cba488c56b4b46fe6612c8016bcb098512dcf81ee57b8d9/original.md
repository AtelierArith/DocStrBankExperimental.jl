```
res2tep(results::Vector{Result}; name="tep", class="res2tep") -> t::TEPperiodic
res2tep(resultfile::AbstractString; name="tep", class="res2tep") -> t::TEPperiodic
res2tep(results::Vector{Result}, tepfile::AbstractString; name="tep", class="res2tep") -> t::TEPperiodic
res2tep(resultfile::AbstractString, tepfile::AbstractString; name="tep", class="res2tep") -> t::TEPperiodic
```

Convert a vector of `Result` elements into a `TEPperiodic` object, as defined in the  [TicraUtilities](https://github.com/simonp0420/TicraUtilities.jl) package.  If positional argument `tepfile` is provided, the `TEPperiodic` object will be saved to this file name as a TICRA-compatible TEP (tabulated electrical properties) file. If the first positional argument is an `AbstractString`, it is  assumed to be the name of a PSSFSS results file, from which the vector of results will be read. The keyword arguments are used to provide values for the same-named fields in the TEP structure.

## Requirements for TEP File Compatibility

Because a TEP file contains all of the information of the full 4×4 scattering matrix computed by PSSFSS, there are no limitations on the type of unit cell geometry that can be used for creating TEP files.

TEP files use the concept of "front" and "rear" incidence.  When converting a PSSFSS analysis result to TEP format, Region 1  (the first layer in the `strata` vector) is taken as the "front" incidence region, and Region `n` (the last layer) is  taken to be the "rear" region.  Both of these layers should have zero width and assume vacuum electrical parameters.  I.e., they should be specified as `Layer()` in the `strata` stackup.

`results` (or `resultfile`) must contain the results of a PSSFSS analysis sweep over θ and ϕ (and possibly frequency) such that

1. Incidence angles θ and ϕ rather than incremental phasings ψ₁ and ψ₂ were used.
2. If more than one ϕ value is used, then all ϕ values in the range `0:Δϕ:(360-Δϕ)` must be present.
3. The entire 3-dimensional Cartesian product of all angles and frequencies must be present.
