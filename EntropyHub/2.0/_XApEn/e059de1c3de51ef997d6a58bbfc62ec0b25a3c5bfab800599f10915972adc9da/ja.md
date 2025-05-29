```
  XAp, Phi = XApEn(Sig1, Sig2)
```

`XAp`（交差近似エントロピー推定値）と、`Sig1`および`Sig2`に含まれるデータ系列に対して推定された一致ベクトルの平均数（`Phi`）を返します。デフォルトのパラメータを使用して、m = [0,1,2] の場合です：埋め込み次元 = 2、時間遅延 = 1、半径距離閾値 = 0.2*SDpooled(`Sig1`,`Sig2`)、対数 = 自然対数。

**注意**：XApEnは方向依存です。したがって、`Sig1`はテンプレートデータ系列として使用され、`Sig2`は一致する系列です。``

```
  XAp, Phi = XApEn(Sig1::Union{AbstractMatrix{T}, AbstractVector{T}} where T<:Real, Sig2::Union{AbstractVector{T} where T<:Real, Nothing} = nothing; m::Int=2, tau::Int=1, r::Union{Real,Nothing}=nothing, Logx::Real=exp(1))
```

指定された「キーワード」引数を使用して、`Sig1`および`Sig2`に含まれるデータ系列間の交差近似エントロピー推定値（`XAp`）を返します：

# 引数：

`m`     - 埋め込み次元、正の整数  [デフォルト: 2] 

`tau`   - 時間遅延、正の整数        [デフォルト: 1]  

`r`     - 半径距離閾値、正のスカラー [デフォルト: 0.2*SDpooled(`Sig1`,`Sig2`)] 

`Logx`  - 対数の底、正のスカラー     [デフォルト: 自然]  

# 参照： `XSampEn`, `XFuzzEn`, `XMSEn`, `ApEn`, `SampEn`, `MSEn`

# 参考文献：

```
  [1] Steven Pincus and Burton H. Singer,
      "Randomness and degrees of irregularity." 
      Proceedings of the National Academy of Sciences 
      93.5 (1996): 2083-2088.

  [2] Steven Pincus,
      "Assessing serial irregularity and its implications for health."
      Annals of the New York Academy of Sciences 
      954.1 (2001): 245-267.
```
