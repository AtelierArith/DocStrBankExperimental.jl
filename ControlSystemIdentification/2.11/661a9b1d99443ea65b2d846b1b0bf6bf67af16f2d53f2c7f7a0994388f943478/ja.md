```
residuals(ARX::TransferFunction, d::InputOutputData)
```

ARXプロセスとInputOutputData dの残差 `v = Ay - Bu` を計算します。返される残差の長さは `length(d) - max(na, nb)` です。

# 例:

```jldoctest
julia> ARX = tf(1, [1, -1], 1)
TransferFunction{Discrete{Int64}, ControlSystemsBase.SisoRational{Int64}}
  1
-----
z - 1

Sample Time: 1 (seconds)
離散時間伝達関数モデル

julia> u = 1:5
1:5

julia> y = lsim(ARX, u, 1:5)[1][:]
5-element Vector{Float64}:
  0.0
  1.0
  3.0
  6.0
 10.0

julia> d = iddata(y, u)
長さ5のInputOutputデータ、出力1、入力1

julia> residuals(ARX, d)
4-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0
```
