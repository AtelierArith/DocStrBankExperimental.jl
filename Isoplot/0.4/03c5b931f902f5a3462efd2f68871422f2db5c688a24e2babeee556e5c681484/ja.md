```julia
yorkfit(x::Collection, σx::Collection, y::Collection, σy::Collection, [r])
yorkfit(x::Collection{<:Measurement}, y::Collection{<:Measurement}, [r])
yorkfit(d::Collection{<:AbstractAnalysis})
```

York (1968) の二次元最小二乗フィットを使用して、`x`、`y`、不確かさ `σx`、および `σy` が与えられたときの方程式 `y = a + bx` のために `a`、`b`、および不確かさ `σa`、`σb` を計算します。オプションで共分散 `r` も考慮されます。

さらなる参考文献として、York, Derek (1968) "Least squares fitting of a straight line with correlated errors" Earth and Planetary Science Letters 5, 320-324. doi: 10.1016/S0012-821X(68)80059-7 を参照してください。

### 例

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
