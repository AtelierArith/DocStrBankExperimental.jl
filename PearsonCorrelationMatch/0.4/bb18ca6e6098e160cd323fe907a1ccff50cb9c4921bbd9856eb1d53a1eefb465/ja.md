```
pearson_match(R::AbstractMatrix{<:Real}, margins; n::Real=12, m::Real=128, kwargs...)
```

ペアワイズでピアソン相関係数を計算し、二変量ガウスコピュラで使用します。結果の行列が有効な相関行列であることを保証します。

# フィールド

  * `R`: 周辺分布のターゲット相関行列。
  * `margins`: 周辺分布のリスト。
  * `n`: 一致する相関を推定するために使用される多項式の次数。
  * `m`: エルミート多項式補間に使用される点の数。
  * `kwargs`: 追加のキーワード引数。現在は未使用。

# 例

```julia-repl
julia> using Distributions

julia> margins = [Beta(2, 3), Uniform(0, 1), Binomial(20, 0.2)];

julia> rho = [
    1.0 0.3 0.6
    0.3 1.0 0.4
    0.6 0.4 1.0
];

julia> pearson_match(rho, margins)
3×3 Matrix{Float64}:
 1.0       0.309111  0.612753
 0.309111  1.0       0.418761
 0.612753  0.418761  1.0
```
