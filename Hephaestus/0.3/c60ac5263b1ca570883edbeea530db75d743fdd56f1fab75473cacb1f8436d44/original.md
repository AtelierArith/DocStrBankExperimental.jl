```
struct ElasticBucklingAnalysis <: AbstractAnalysisType
```

A type representing the elastic buckling analysis.

To perform an elastic buckling analysis, use the following command:

```julia
solution = solve(model, ElasticBucklingAnalysis())
```
