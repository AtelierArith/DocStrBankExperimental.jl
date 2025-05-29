```
XSamp, A, B = XSampEn(Sig1, Sig2)
```

`XSamp`（クロスサンプルエントロピー推定値）と、`Sig1` と `Sig2` に含まれる2つの単変量データ系列のための一致したベクトルの数（m:B, m+1:A）を返します。ここで、m = [0,1,2] であり、デフォルトのパラメータを使用して推定されます：埋め込み次元 = 2、時間遅延 = 1、半径距離閾値 = 0.2*SDpooled(`Sig1`,`Sig2`)、対数 = 自然対数

```
XSamp, A, B, (Vcp, Ka, Kb) = XSampEn(Sig1, Sig2, ..., Vcp = true)
```

`Vcp == true` の場合、クロスサンプルエントロピー推定値 (`XSamp`) と一致した状態ベクトルの数 (`m: B`, `m+1: A`) に加えて、追加のタプル `(Vcp, Ka, Kb)` が返されます。`(Vcp, Ka, Kb)` には条件付き確率の分散 (`Vcp`)、すなわち CP = A/B、及び長さ m+1 の **重複する** 一致ベクトルペアの数 (`Ka`) と長さ m の (`Kb`) が含まれます。注意：`Vcp` はゼロ次の埋め込み次元 (m = 0) では未定義であり、計算要求のため、**関数の出力を返すのにかなりの時間がかかります。** 詳細は [2] の付録Bを参照してください。

```
XSamp, A, B = XSampEn(Sig1::Union{AbstractMatrix{T}, AbstractVector{T}} where T<:Real, Sig2::Union{AbstractVector{T} where T<:Real, Nothing} = nothing; m::Int=2, tau::Int=1, r::Union{Real,Nothing}=nothing, Logx::Real=exp(1), Vcp::Bool=false)
```

指定された 'キーワード' 引数を使用して、`Sig1` と `Sig2` のデータ系列間で推定された次元 [0,1,...,m] のクロスサンプルエントロピー推定値 (`XSamp`) を返します。

# 引数:

`m`     - 埋め込み次元、正の整数  [デフォルト: 2]   

`tau`   - 時間遅延、正の整数         [デフォルト: 1]   

`r`     - 半径距離閾値、正のスカラー [デフォルト: 0.2*SDpooled(`Sig1`,`Sig2`)] 

`Logx`  - 対数の底、正のスカラー      [デフォルト: 自然] 

`Vcp`   - 条件付き確率の分散と重複する一致ベクトルペアの数を返すオプション 

`XFuzzEn`、`XApEn`、`SampEn`、`SampEn2D`、`XMSEn`、`ApEn` も参照してください。

# 参考文献:

```
[1] Joshua S Richman and J. Randall Moorman. 
    "Physiological time-series analysis using approximate entropy
    and sample entropy." 
    American Journal of Physiology-Heart and Circulatory Physiology
    (2000)

[2] Douglas E Lake, Joshua S Richman, M.P. Griffin, J. Randall Moorman
    "Sample entropy analysis of neonatal heart rate variability."
    American Journal of Physiology-Regulatory, Integrative and Comparative Physiology
    283, no. 3 (2002): R789-R797.
```
