```
hasnonfrequencydimension(spectrum)
```

Return true if the spectrum contains a non-frequency domain dimension.

# Example

```julia
julia> y2=loadnmr("exampledata/2D_HN/test.ft2");
julia> hasnonfrequencydimension(y2)
false
julia> y3=loadnmr("exampledata/pseudo3D_HN_R2/ft/test%03d.ft2");
julia> hasnonfrequencydimension(y3)
true
```
