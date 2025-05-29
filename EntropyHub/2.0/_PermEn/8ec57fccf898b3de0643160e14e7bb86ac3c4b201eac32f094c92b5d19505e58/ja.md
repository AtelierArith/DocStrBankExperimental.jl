```
Perm, Pnorm, cPE = PermEn(Sig)
```

データ系列 `Sig` から推定された順列エントロピーの推定値 `Perm`、正規化された順列エントロピー `Pnorm`、条件付き順列エントロピー `cPE` を返します。デフォルトのパラメータを使用して、`m` = [1,2] で推定されます：埋め込み次元 = 2、時間遅延 = 1、対数 = 基数 2、正規化 = シンボル数に対して（`m`-1）。注意：標準の PermEn 推定を使用すると、`Perm` = 0 となります（`m` = 1 の場合）。注意：信号の長さは 5m より大きいことが推奨されます！ （[8] および Amigo et al., Europhys. Lett. 83:60005, 2008 を参照）

```
Perm, Pnorm, cPE = PermEn(Sig, m)
```

指定された埋め込み次元 = [1,...,`m`] を使用して、データ系列 `Sig` から推定された順列エントロピーの推定値 `Perm` を返します。他のデフォルトパラメータは上記の通りです。

```
Perm, Pnorm, cPE = PermEn(Sig::AbstractArray{T,1} where T<:Real; m::Int=2, tau::Int=1, Typex::String="none", tpx::Union{Real,Nothing}=nothing, Logx::Real=2, Norm::Bool=false)
```

指定された 'キーワード' 引数を使用して、データ系列 `Sig` から推定された次元 = [1,...,`m`] の順列エントロピーの推定値 `Perm` を返します。

# 引数:

`m`     - 埋め込み次元、1 より大きい整数 

`tau`   - 時間遅延、正の整数

`Logx`  - 対数の基数、正のスカラー（自然対数の場合は 0 を入力） 

`Norm`  - PermEn 値の正規化：

```
      false -  順列シンボルの対数（[m-1]）に対して正規化 - デフォルト
      true  -  すべての可能な順列の対数（[m!]）に対して正規化
      * 注意：正規化された順列エントロピーは m = 1 の場合は未定義です。
      ** 注意：Typex = 'uniquant' かつ Norm = true の場合、正規化
      は log(tpx^m) に対して計算されます。
```

`Typex`  - 順列エントロピーの変種、次のいずれか：           {`"none", "uniquant", "finegrain", "modified", "ampaware",           "weighted", "edge", "phase"}           PermEn の変種に関する詳細は EntropyHub ガイドを参照してください。    

`tpx`   - 関連する順列エントロピーの変種の調整パラメータ。

```
      [uniquant]  'tpx' は L パラメータ、1 より大きい整数（デフォルト = 4）。           
      [finegrain] 'tpx' はアルファパラメータ、正のスカラー（デフォルト = 1）
      [ampaware]  'tpx' は A パラメータ、範囲 [0 1] の値（デフォルト = 0.5）
      [edge]      'tpx' は r 感度パラメータ、0 より大きいスカラー（デフォルト = 1）
      [phase]     'tpx' は tpx==1 のとき瞬時の位相（解析信号の角度）をアンラップします（デフォルト = 0）
      PermEn の変種に関する詳細は EntropyHub ガイドを参照してください。
```

# 参照： `XPermEn`, `MSEn`, `XMSEn`, `SampEn`, `ApEn`, `CondEn`

# 参考文献:

```
[1] Christoph Bandt and Bernd Pompe, 
        "Permutation entropy: A natural complexity measure for time series." 
        Physical Review Letters,
        88.17 (2002): 174102.

[2] Xiao-Feng Liu, and Wang Yue,
        "Fine-grained permutation entropy as a measure of natural 
        complexity for time series." 
        Chinese Physics B 
        18.7 (2009): 2690.

[3] Chunhua Bian, et al.,
        "Modified permutation-entropy analysis of heartbeat dynamics."
        Physical Review E
        85.2 (2012) : 021906

[4] Bilal Fadlallah, et al.,
        "Weighted-permutation entropy: A complexity measure for time 
        series incorporating amplitude information." 
        Physical Review E 
        87.2 (2013): 022911.

[5] Hamed Azami and Javier Escudero,
        "Amplitude-aware permutation entropy: Illustration in spike 
        detection and signal segmentation." 
        Computer methods and programs in biomedicine,
        128 (2016): 40-51.

[6] Zhiqiang Huo, et al.,
        "Edge Permutation Entropy: An Improved Entropy Measure for 
        Time-Series Analysis," 
        45th Annual Conference of the IEEE Industrial Electronics Soc,
        (2019), 5998-6003

[7] Zhe Chen, et al. 
        "Improved permutation entropy for measuring complexity of time
        series under noisy condition." 
        Complexity 
        1403829 (2019).

[8] Maik Riedl, Andreas Müller, and Niels Wessel,
        "Practical considerations of permutation entropy." 
        The European Physical Journal Special Topics 
        222.2 (2013): 249-262.

[9] Kang Huan, Xiaofeng Zhang, and Guangbin Zhang,
        "Phase permutation entropy: A complexity measure for nonlinear time 
        series incorporating phase information." 
        Physica A: Statistical Mechanics and its Applications 
        568 (2021): 125686.
```
