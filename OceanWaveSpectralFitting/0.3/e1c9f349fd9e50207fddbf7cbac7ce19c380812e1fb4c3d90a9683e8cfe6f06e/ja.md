```
JONSWAP{K}(α,ωₚ,γ,r)
JONSWAP{K}(x)
```

垂直変位のための4パラメータJONSWAPモデル。

# 型パラメータ

型パラメータ`K`は、エイリアシングの量を表す非負整数です。これは、一部のデバイスに高域通過フィルターがあり、記録された系列に存在するエイリアシングの量を制限するために便利です。特に、`Δ`秒ごとに記録された系列に対する`JONSWAP{K}`モデルは、`Δ`秒ごとにサンプリングされ、`(2K-1)π/Δ`で高域通過フィルターがかけられた系列に適しています。

# 引数

  * `α`: スケールパラメータ。
  * `ωₚ`: ピーク角周波数。
  * `γ`: ピーク強化係数。
  * `r`: テール減衰指数。

# ベクトルコンストラクタ引数

  * `x`: パラメータのベクトル `[α,ωₚ,γ,r]`。

# 背景

JONSWAPスペクトル密度関数は次のようになります。

$$
f(ω) = αω^{-r}\exp\left \{-\frac{r}{4}\left(\frac{|ω|}{ωₚ}\right)^{-4}\right \}γ^{δ(|ω|)}
$$

ここで、

$$
δ(ω) = \exp\left\{-\tfrac{1}{2 (0.07+0.02\cdot\mathbb{1}_{ωₚ>|ω|})^2}\left (\tfrac{|ω|}{ωₚ}-1\right )^2\right\}.
$$
