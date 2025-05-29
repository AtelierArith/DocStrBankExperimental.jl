```
Div, CDEn, Bm = DivEn(Sig)
```

データシーケンス（`Sig`）から推定された多様性エントロピー（`Div`）、累積多様性エントロピー（`CDEn`）、および対応する確率（`Bm`）を返します。デフォルトのパラメータを使用します：埋め込み次元 = 2、時間遅延 = 1、#ビン = 5、対数 = 自然対数、

```
Div, CDEn, Bm = DivEn(Sig::AbstractArray{T,1} where T<:Real; m::Int=2, tau::Int=1, r::Int=5, Logx::Real=exp(1))
```

指定された「キーワード」引数を使用してデータシーケンス（`Sig`）から推定された多様性エントロピー（`Div`）を返します：

# 引数：

`m`     - 埋め込み次元、1より大きい整数   

`tau`   - 時間遅延、正の整数    

`r`     - ヒストグラムビン #: いずれか 

```
        * ビンの数を表す整数 [1 < `r`]
        * ビンのエッジを表す3つ以上の増加する値のリスト/NumPy配列 [-1 1]の範囲に含まれる右端のエッジを含む。
```

`Logx`  - 対数の底、正のスカラー（自然対数の場合は0を入力）

# 参照： `CoSiEn`, `PhasEn`, `SlopEn`, `GridEn`, `MSEn`

# 参考文献：

```
[1] X. Wang, S. Si and Y. Li, 
    "Multiscale Diversity Entropy: A Novel Dynamical Measure for Fault 
    Diagnosis of Rotating Machinery," 
    IEEE Transactions on Industrial Informatics,
    vol. 17, no. 8, pp. 5419-5429, Aug. 2021
    
[2] Y. Wang, M. Liu, Y. Guo, F. Shu, C. Chen and W. Chen, 
    "Cumulative Diversity Pattern Entropy (CDEn): A High-Performance, 
    Almost-Parameter-Free Complexity Estimator for Nonstationary Time Series,"
    IEEE Transactions on Industrial Informatics
    vol. 19, no. 9, pp. 9642-9653, Sept. 2023
```
