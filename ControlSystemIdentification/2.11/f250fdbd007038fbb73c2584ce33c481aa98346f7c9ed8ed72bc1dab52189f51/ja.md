```
G, H, e = arxar(d::InputOutputData, na::Int, nb::Union{Int, Vector{Int}}, nd::Int)
```

ARXARモデル `Ay = Bu + v` を推定します。ここで、`v = He` であり、`H = 1/D` です。一般化最小二乗法を使用します。

ARXARの略語は「外因性入力を持つ二変量パラメトリック自己回帰モデル」を意味します。詳細については、Söderström - 一般化最小二乗識別法の収束特性、1974年を参照してください。

# 引数:

  * `d`: iddata
  * `na`: Aの次数
  * `nb`: Bの係数の数、次数は `nb + inputdelay - 1` によって決まります。MISO推定では、`nb = [nb₁, nb₂...]` の形を取ります。
  * `nd`: Dの次数

# キーワード引数:

  * `H = nothing`: ARノイズモデルに関する事前知識
  * `inputdelay = ones(Int, size(nb))`: 入力のオプション遅延、inputdelay = 0 は直接項を結果します。MISO推定では、inputdelay = [d₁, d₂...] の形を取ります。
  * `λ = 0`: `λ > 0` はL₂正則化のために提供できます。
  * `estimator = \`: 例: `\,tls,irls,rtls`、後者の3つは `using TotalLeastSquares` を必要とします。
  * `δmin = 10e-4`: eのパワーの最小変化、収束を指定します。
  * `iterations = 10`: 最大反復回数。
  * `verbose = false`: trueの場合、より多くの情報が印刷されます。

[`plr`](@ref) や [`arx`](@ref) も参照してください。

# 例:

```
julia> N = 500 
500

julia> sim(G, u) = lsim(G, u, 1:N)[1][:]
sim (generic function with 1 method)

julia> A = tf([1, -0.8], [1, 0], 1)
TransferFunction{Discrete{Int64}, ControlSystemsBase.SisoRational{Float64}}
1.0z - 0.8
----------
   1.0z

サンプル時間: 1 (秒)
離散時間伝達関数モデル

julia> B = tf([0, 1], [1, 0], 1)
TransferFunction{Discrete{Int64}, ControlSystemsBase.SisoRational{Int64}}
1
-
z

サンプル時間: 1 (秒)
離散時間伝達関数モデル

julia> G = minreal(B / A)
TransferFunction{Discrete{Int64}, ControlSystemsBase.SisoRational{Float64}}
   1.0
----------
1.0z - 0.8

サンプル時間: 1 (秒)
離散時間伝達関数モデル

julia> D = tf([1, 0.7], [1, 0], 1)
TransferFunction{Discrete{Int64}, ControlSystemsBase.SisoRational{Float64}}
1.0z + 0.7
----------
   1.0z

サンプル時間: 1 (秒)
離散時間伝達関数モデル

julia> H = 1 / D
TransferFunction{Discrete{Int64}, ControlSystemsBase.SisoRational{Float64}}
   1.0z
----------
1.0z + 0.7

サンプル時間: 1 (秒)
離散時間伝達関数モデル

julia> u, e = randn(1, N), randn(1, N)
[...]

julia> y, v = sim(G, u), sim(H * (1/A), e) # プロセスをシミュレート
[...]

julia> d = iddata(y .+ v, u, 1)
入力出力データの長さ500、出力1、入力1

julia> na, nb , nd = 1, 1, 1
(1, 1, 1)

julia> Gest, Hest, res = arxar(d, na, nb, nd)
(G = TransferFunction{Discrete{Int64}, ControlSystemsBase.SisoRational{Float64}}
   0.9987917259291642
-------------------------
1.0z - 0.7937837464682017

サンプル時間: 1 (秒)
離散時間伝達関数モデル, H = TransferFunction{Discrete{Int64}, ControlSystemsBase.SisoRational{Float64}}
          1.0z
-------------------------
1.0z + 0.7019519225937721

サンプル時間: 1 (秒)
離散時間伝達関数モデル, e = [...]
```
