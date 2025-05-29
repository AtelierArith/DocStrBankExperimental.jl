```
EoE, AvEn, S2 = EnofEn(Sig)
```

データシーケンス（`Sig`）から推定されたすべてのウィンドウにわたるエントロピーのエントロピー（`EoE`）、平均シャノンエントロピー（`AvEn`）、およびレベルの数（`S2`）を返します。デフォルトのパラメータを使用します：ウィンドウの長さ（サンプル）= 10、スライス = 10、対数 = 自然、心拍間隔範囲（xmin, xmax）= (min(Sig), max(Sig))

```
EoE, AvEn, S2 = EnofEn(Sig::AbstractArray{T,1} where T<:Real; tau::Int=10, S::Int=10, Xrange::Tuple{Real,REal}, Logx::Real=exp(1))
```

指定された「キーワード」引数を使用してデータシーケンス（`Sig`）から推定されたエントロピーのエントロピー（`EoE`）を返します：

# 引数：

`tau`    - ウィンドウの長さ、1より大きい整数 

`S`      - スライスの数（s1,s2）、2より大きい整数の二要素タプル 

`Xrange` - 心拍間隔の最小値と最大値、X[1] <= X[2] の二要素タプル

`Logx`   - 対数の底、正のスカラー  

# 参照： `SampEn`, `MSEn`, `ApEn`

# 参考文献：

```
[1] Chang Francis Hsu, et al.,
    "Entropy of entropy: Measurement of dynamical complexity for
    biological systems." 
    Entropy 
    19.10 (2017): 550.
```
