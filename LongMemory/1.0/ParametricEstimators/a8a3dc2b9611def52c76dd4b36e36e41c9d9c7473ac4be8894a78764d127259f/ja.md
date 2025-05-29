```
har_est(x::Array; m::Array = [1 , 5 , 22])
```

データ `x` に基づいて、異質自己回帰（HAR）モデルのパラメータを推定します。詳細は [Corsi (2009)](https://academic.oup.com/jfec/article/7/2/174/856522) を参照してください。

# 引数

  * `x::Array`: データ。

# オプション引数

  * `m::Array`: 推定に使用するラグの配列。デフォルトでは、ラグは1、5、22であり、これは元の論文で提案されたものです。

# 出力

  * `β::Array`: HARモデルの推定パラメータ。
  * `σ::Real`: HARモデルの推定標準偏差。

# 例

```julia
julia> har_est(randn(100,1))
```
