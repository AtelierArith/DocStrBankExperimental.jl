```julia
preambleCache(dfg, vars, usrfnc)

```

Overload for specific factor preamble usage.

Notes:

  * See https://github.com/JuliaRobotics/IncrementalInference.jl/issues/1462

DevNotes

  * Integrate into CalcFactor

      * Add threading

Example:

```julia
import IncrementalInference: preableCache

preableCache(dfg::AbstractDFG, vars::AbstractVector{<:DFGVariable}, usrfnc::MyFactor) = MyFactorCache(randn(10))

# continue regular use, e.g.
mfc = MyFactor(...)
addFactor!(fg, [:a;:b], mfc)
# ... 
```
