```julia
yorkfit(x::Collection, σx::Collection, y::Collection, σy::Collection, [r])
yorkfit(x::Collection{<:Measurement}, y::Collection{<:Measurement}, [r])
yorkfit(d::Collection{<:AbstractAnalysis})
```

Uses the York (1968) two-dimensional least-squares fit to calculate `a`, `b`, and uncertanties `σa`, `σb` for the equation `y = a + bx`, given `x`, `y`, uncertaintes `σx`, and `σy`, and optially covarances `r`.

For further reference, see: York, Derek (1968) "Least squares fitting of a straight line with correlated errors" Earth and Planetary Science Letters 5, 320-324. doi: 10.1016/S0012-821X(68)80059-7

### Examples

```julia
julia> x = (1:100) .+ randn.();

julia> y = 2*(1:100) .+ randn.();

julia> yorkfit(x, ones(100), y, ones(100))
YorkFit{Float64}:
Least-squares linear fit of the form y = a + bx where
  intercept a : -0.29 ± 0.2 (1σ)
  slope b     : 2.0072 ± 0.0035 (1σ)
  MSWD        : 0.8136665223891004
```
