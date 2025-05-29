```
printResultInfo(result)
```

Print info about result.

# Example

```julia
using ModiaResult
using Unitful
ModiaResult.@usingModiaPlot

t = range(0.0, stop=10.0, length=100)
result = OrderedDict{String,Any}("time"=> t*u"s", 
                                 "phi" => sin.(t)*u"rad", 
                                 "A"   => OneValueVector(2.0, length(t)))
printResultInfo(result)

# Gives output:
 # │ name  unit  nTime  signalType  valueSize  eltype
───┼───────────────────────────────────────────────────
 1 │ time  s     100    Independent ()         Float64
 2 │ phi   rad   100    Continuous  ()         Float64
 3 | A           100*   Continuous  ()         Float64
 *: Signal stored as ModiaResult.OneValueVector (e.g. parameter)
```
