function rxdetect(X::Matrix{T}, alpha::Float64 = 0.99)

データを行列の形で受け取り、最初のインデックスが実現、2番目が特徴（マージナル）に対応します。RX（Reed-Xiaoli）異常検出を使用して、外れ値の実現に対応するBoolの配列を返します。alphaはRX検出器の感度パラメータです。

```jldoctest
julia> Random.seed!(42);

julia> x = vcat(rand(8,2), 20*rand(2,2))
10×2 Array{Float64,2}:
  0.533183    0.956916
  0.454029    0.584284
  0.0176868   0.937466
  0.172933    0.160006
  0.958926    0.422956
  0.973566    0.602298
  0.30387     0.363458
  0.176909    0.383491
 11.8582      5.25618
 14.9036     10.059

julia> rxdetect(x, 0.95)
10-element Array{Bool,1}:
 false
 false
 false
 false
 false
 false
 false
 false
  true
  true
```
