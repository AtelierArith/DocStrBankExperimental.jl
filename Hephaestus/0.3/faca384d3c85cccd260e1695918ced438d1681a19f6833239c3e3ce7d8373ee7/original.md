```
struct FreeVibrationAnalysis <: AbstractAnalysisType
```

A type representing the free vibration analysis.

To perform an free vibration analysis, use the following command:

```julia
solution = solve(model, FreeVibrationAnalysis())
```
