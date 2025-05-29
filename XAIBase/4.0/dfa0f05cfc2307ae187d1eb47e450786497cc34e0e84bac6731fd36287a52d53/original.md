```
analyze(input, method)
analyze(input, method, output_selection)
```

Apply the analyzer `method` for the given input, returning an [`Explanation`](@ref). If `output_selection` is specified, the explanation will be calculated for that output. Otherwise, the output with the highest activation is automatically chosen.

See also [`Explanation`](@ref).
