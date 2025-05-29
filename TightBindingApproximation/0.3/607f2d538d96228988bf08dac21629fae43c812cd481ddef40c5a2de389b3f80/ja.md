```
BerryCurvatureData{R<:ReciprocalSpace, C<:Array{Float64}, N<:Union{Vector{Float64}, Float64, Nothing}} <: Data
```

ベリー曲率のデータ、含まれるもの：

1. `reciprocalspace::R`: ベリー曲率が計算される逆空間。
2. `values::C`: 特定のバンドセットに対するベリー曲率。
3. `chernnumber::N`: `nothing`でない場合、ベクトルのときは各エネルギーバンドのチェルン数、数値のときはすべてのバンドの合計チェルン数。
