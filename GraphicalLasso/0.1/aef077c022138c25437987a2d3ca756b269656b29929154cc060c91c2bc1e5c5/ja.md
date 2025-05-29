```
ebic(θ, ll, obs, thr, γ)
```

与えられた精度行列 `θ` に対する拡張ベイズ情報基準 (EBIC) を計算します。Foygel と Drton (2010) の論文に基づき、EBIC は次のように定義されます：

$$
\text{EBIC} = -2 \times \text{Log-likelihood} + \log(n) \times \mathbf{E} + 4 \times \gamma \times \mathbf{E} \times \log(p)
$$

ここで：

  * n は観測の数です。
  * p は変数の数です。
  * gamma は調整パラメータです。
  * エッジの数は、指定された閾値を超える theta のエントリのカウントとして計算されます。

# 引数

  * `θ::AbstractMatrix`: 精度行列。
  * `ll::Real`: 対数尤度。
  * `obs::Int`: 観測の数。
  * `thr::Real`: エッジをカウントするための閾値。
  * `γ::Real`: EBIC 調整パラメータ。

# 戻り値

  * `Real`: EBIC 値。

```
