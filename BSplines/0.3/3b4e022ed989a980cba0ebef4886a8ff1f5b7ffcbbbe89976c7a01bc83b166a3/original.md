```
interpolate(basis::BSplineBasis, xvalues, yvalues; indices=eachindex(basis)) -> Spline
```

Interpolate the data given by `xvalues` and `yvalues` in the B-spline basis `basis`. If `indices` is supplied, only the basis functions at the given indices of `basis` are used.

The spline interpolation is calculated by creating the matrix `B = [basis[i](x) for x=xvalues, i=indices]` and then calculating `B\yvalues`.

See also: [`approximate`](@ref)

# Examples

```jldoctest
julia> basis = BSplineBasis(5, 1:10);

julia> xs = range(1, stop=10, length=length(basis)); ys = log.(xs);

julia> spl = interpolate(basis, xs, ys)
BSplines.Spline{BSplines.BSplineBasis{UnitRange{Int64}}, Vector{Float64}}:
 basis: 13-element BSplineBasis{UnitRange{Int64}}:
  order: 5
  breakpoints: 1:10
 coeffs: [0.0, 0.248019, 0.596872, 0.946671, 1.26894, 1.51405, 1.71149, 1.87666, 2.01856, 2.14292, 2.22592, 2.27758, 2.30259]

julia> spl(float(ℯ))
0.9999766059171411
```
