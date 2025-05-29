```
XK2, Ci = XK2En(Sig1, Sig2)
```

`Sig1` と `Sig2` に含まれるデータ系列の間で推定されたクロス・コルモゴロフエントロピー推定値 (`XK2`) と相関積分 (`Ci`) を返します。デフォルトのパラメータを使用して推定されます：埋め込み次元 = 2、時間遅延 = 1、距離閾値 (r) = 0.2*SDpooled(Sig1, Sig2)、対数 = 自然対数

```
XK2, Ci = XK2En(Sig1::Union{AbstractMatrix{T}, AbstractVector{T}} where T<:Real, Sig2::Union{AbstractVector{T} where T<:Real, Nothing} = nothing; m::Int=2, tau::Int=1, r::Union{Real,Nothing}=nothing, Logx::Real=exp(1))
```

指定された「キーワード」引数を使用して、`Sig1` と `Sig2` に含まれるデータ系列の間で推定されたクロス・コルモゴロフエントロピー推定値 (`XK2`) を返します。

# 引数:

`m`     - 埋め込み次元、正の整数 [デフォルト: 2]  

`tau`   - 時間遅延、正の整数         [デフォルト: 1]  

`r`     - 半径距離閾値、正のスカラー  [デフォルト: 0.2*SDpooled(`Sig1`,`Sig2`)]  

`Logx`  - 対数の底、正のスカラー      [デフォルト: 自然]  

# 参照: `XSampEn`, `XFuzzEn`, `XApEn`, `K2En`, `XMSEn`, `XDistEn`

# 参考文献:

```
[1]  Matthew W. Flood,
     "XK2En - EntropyHub Project"
     (2021) https://github.com/MattWillFlood/EntropyHub
```
