```
K2, Ci = K2En(Sig)
```

データ系列 `Sig` からデフォルトのパラメータを使用して推定されたコルモゴロフエントロピーの推定値 `K2` と相関積分 `Ci` を返します：埋め込み次元 = 2、時間遅延 = 1、r = 0.2*SD(`Sig`)、対数 = 自然対数

```
K2, Ci = K2En(Sig::AbstractArray{T,1} where T<:Real; m::Int=2, tau::Int=1, r::Real=0.2*std(Sig,corrected=false), Logx::Real=exp(1))
```

データ系列 `Sig` から推定された次元 = [1,...,`m`] のコルモゴロフエントロピーの推定値 `K2` を返します。'キーワード' 引数を使用します：

# 引数：

`m`     - 埋め込み次元、正の整数

`tau`   - 時間遅延、正の整数

`r`     - 半径、正のスカラー 

`Logx`  - 対数の底、正のスカラー

# 参照： `DistEn`, `XK2En`, `MSEn`

# 参考文献：

```
[1] Peter Grassberger and Itamar Procaccia,
    "Estimation of the Kolmogorov entropy from a chaotic signal." 
    Physical review A 28.4 (1983): 2591.

[2] Lin Gao, Jue Wang  and Longwei Chen
    "Event-related desynchronization and synchronization 
    quantification in motor-related EEG by Kolmogorov entropy"
    J Neural Eng. 2013 Jun;10(3):03602
```
