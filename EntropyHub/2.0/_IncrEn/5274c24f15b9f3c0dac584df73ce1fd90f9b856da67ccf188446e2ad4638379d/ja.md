```
Incr = IncrEn(Sig)
```

データ系列（`Sig`）の増分エントロピー（`Incr`）推定値をデフォルトパラメータを使用して返します：埋め込み次元 = 2、時間遅延 = 1、量子化解像度 = 4、対数 = 基数 2、

```
Incr = IncrEn(Sig::AbstractArray{T,1} where T<:Real; m::Int=2, tau::Int=1, R::Int=4, Logx::Real=2, Norm::Bool=false)
```

指定された「キーワード」引数を使用してデータ系列（`Sig`）の増分エントロピー（`Incr`）推定値を返します：

# 引数：

`m`     - 埋め込み次元、1より大きい整数   

`tau`   - 時間遅延、正の整数    

`R`     - 量子化解像度、正のスカラー    

`Logx`  - 対数の基数、正のスカラー（自然対数の場合は0を入力） 

`Norm`  - IncrEn値の正規化： 

```
      [false]  正規化なし - デフォルト
      [true]   埋め込み次元（m-1）に対して正規化します。
```

# 参照： `PermEn`, `SyDyEn`, `MSEn`

# 参考文献：

```
[1] Xiaofeng Liu, et al.,
    "Increment entropy as a measure of complexity for time series."
    Entropy
    18.1 (2016): 22.1.

***   "Correction on Liu, X.; Jiang, A.; Xu, N.; Xue, J. - Increment 
    Entropy as a Measure of Complexity for Time Series,
    Entropy 2016, 18, 22." 
    Entropy 
    18.4 (2016): 133.

[2] Xiaofeng Liu, et al.,
    "Appropriate use of the increment entropy for 
    electrophysiological time series." 
    Computers in biology and medicine 
    95 (2018): 13-23.
```
