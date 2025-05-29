```
ar(d::AbstractIdData, na; λ=0, estimator=\, scaleB=false, stochastic=false)
```

AR伝達関数 `G = 1/A` を推定します。ARプロセスは `A(z⁻¹)y(t) = e(t)` と定義されます。

ARの略語は「自己回帰モデル」を意味します。

# 引数:

  * `d`: IdData, [`iddata`](@ref) を参照
  * `na`: モデルの次数
  * `λ`: `λ > 0` はL₂正則化のために提供できます
  * `estimator`: 例: `\,tls,irls,rtls`
  * `scaleB`: 予測誤差の分散を使用して分子をスケーリングするかどうか。
  * `stochastic`: trueの場合、不確実なパラメータを `MonteCarloMeasurements.Particles` で表現した伝達関数を返します。

最小二乗法を使用したARモデルの推定は、重い測定ノイズに苦しむことが知られており、この場合 `estimator = tls` を使用すると結果が改善される可能性があります。

# 例

```jldoctest
julia> N = 10000
10000

julia> e = [-0.2; zeros(N-1)] # ノイズ e
10000-element Vector{Float64}:
[...]

julia> G = tf([1, 0], [1, -0.9], 1) # AR伝達関数
TransferFunction{Discrete{Int64}, ControlSystemsBase.SisoRational{Float64}}
   1.0z
----------
1.0z - 0.9

サンプル時間: 1 (秒)
離散時間伝達関数モデル

julia> y = lsim(G, e, 1:N)[1][:] # 入力ノイズ e からAR伝達関数の出力を取得
10000-element Vector{Float64}:
[...]

julia> Gest = ar(iddata(y), 1) # 出力 y からAR伝達関数を推定
TransferFunction{Discrete{Float64}, ControlSystemsBase.SisoRational{Float64}}
          1.0z
-------------------------
1.0z - 0.8999999999999998

サンプル時間: 1.0 (秒)
離散時間伝達関数モデル

julia> G ≈ Gest # 推定が正しかったかテスト
true

julia> eest = lsim(1/Gest, y, 1:N)[1][:] # 出力 y と推定伝達関数 Gest から入力ノイズ e を復元
10000-element Vector{Float64}:
[...]

julia> isapprox(eest, e, atol = eps()) # 入力ノイズが正しく復元された
true 
```
