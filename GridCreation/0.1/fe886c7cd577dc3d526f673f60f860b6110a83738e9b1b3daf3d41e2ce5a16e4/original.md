```
cartVecsToPolarGrid(X, Y)
```

Construct a polar grid (ρ,θ) from the row vector X and column vector Y.  Returns a pair of 2D arrays containing the radial and azimuthal coordinates.

# Examples

```julia-repl
julia> X=(-2:1)'; Y=-2:1;
julia> ρ,θ=cartVecsToPolarGrid(X,Y);
julia> ρ
4×4 Array{Float64,2}:
 2.82843  2.23607  2.0  2.23607
 2.23607  1.41421  1.0  1.41421
 2.0      1.0      0.0  1.0
 2.23607  1.41421  1.0  1.41421
julia> θ
4×4 Array{Float64,2}:
 -2.35619  -2.03444  -1.5708  -1.10715
 -2.67795  -2.35619  -1.5708  -0.785398
  3.14159   3.14159   0.0      0.0
  2.67795   2.35619   1.5708   0.785398
```

See also: [`mkCartVecs`](@ref)
