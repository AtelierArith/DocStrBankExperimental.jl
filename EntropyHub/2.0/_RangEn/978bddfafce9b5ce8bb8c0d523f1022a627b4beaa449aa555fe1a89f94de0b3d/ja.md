```
Rangx, A, B = RangEn(Sig)
```

データ系列（`Sig`）からサンプルエントロピーアルゴリズムを使用して推定された範囲エントロピー推定値（`Rangx`）と一致した状態ベクトルの数（`m: B`、`m+1: A`）を返します。デフォルトのパラメータは次のとおりです：埋め込み次元 = 2、時間遅延 = 1、半径閾値 = 0.2、対数 = 自然対数。

```
Rangx, A, B = RangEn(Sig::AbstractArray{T,1} where T<:Real; m::Int=2, tau::Int=1, r::Real=0.2, Methodx::String="SampEn", Logx::Real=exp(1))
```

指定されたキーワード引数を使用してデータ系列（`Sig`）に対して推定された次元 = `m` の範囲エントロピー推定値（`Rangx`）を返します：

# 引数：

`m`         - 埋め込み次元、正の整数

`tau`       - 時間遅延、正の整数

`r`         - 半径距離閾値、0と1の間の正の値

`Methodx`   - 基本エントロピー法、'SampEn' [デフォルト] または 'ApEn'

`Logx`      - 対数の底、正のスカラー  

# 参照： `ApEn`, `SampEn`, `FuzzEn`,  `MSEn`

# 参考文献：

```
[1] Omidvarnia, Amir, et al.
    "Range entropy: A bridge between signal complexity and self-similarity"
    Entropy 
    20.12 (2018): 962.
    
[2] Joshua S Richman and J. Randall Moorman. 
    "Physiological time-series analysis using approximate entropy
    and sample entropy." 
    American Journal of Physiology-Heart and Circulatory Physiology 
    2000
```
