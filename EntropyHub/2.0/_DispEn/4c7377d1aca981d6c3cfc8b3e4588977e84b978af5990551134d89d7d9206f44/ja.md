```
Dispx, RDE = DispEn(Sig)
```

データ系列（`Sig`）から推定された分散エントロピー（`Dispx`）と逆分散エントロピー（`RDE`）を返します。デフォルトのパラメータを使用します：埋め込み次元 = 2、時間遅延 = 1、シンボル = 3、対数 = 自然、データ変換 = 正規化累積分布関数（ncdf）

```
Dispx, RDE = DispEn(Sig::AbstractArray{T,1} where T<:Real; c::Int=3, m::Int=2, tau::Int=1, Typex::String="ncdf", Logx::Real=exp(1), Fluct::Bool=false, Norm::Bool=false, rho::Real=1)
```

指定された「キーワード」引数を使用してデータ系列（`Sig`）から推定された分散エントロピー（`Dispx`）と逆分散エントロピー（`RDE`）を返します：

# 引数：

`m`     - 埋め込み次元、正の整数

`tau`   - 時間遅延、正の整数

`c`     - シンボルの数、1より大きい整数

`Typex` - データからシンボリック系列への変換のタイプ、次のいずれか：           {`"linear", "kmeans" ,"ncdf", "finesort", "equal"`}

```
      これらの変換に関する詳細はEntropyHubガイドを参照してください。
```

`Logx`  - 対数の底、正のスカラー

`Fluct` - Fluct == true の場合、DispEnは変動ベースの分散エントロピーを返します。   [デフォルト：false]

`Norm`  - DispxとRDE値の正規化：           [false]  正規化なし - デフォルト           [true]   可能な分散パターンの数に対して正規化                     (c^m  または (2c -1)^m-1 もし Fluct == true の場合)。

`rho`   - *Typex == 'finesort' の場合、rhoは調整パラメータです*（デフォルト：1）

# `PermEn`、`SyDyEn`、`MSEn` も参照してください

# 参考文献：

```
[1] Mostafa Rostaghi and Hamed Azami,
    "Dispersion entropy: A measure for time-series analysis." 
    IEEE Signal Processing Letters 
    23.5 (2016): 610-614.

[2] Hamed Azami and Javier Escudero,
    "Amplitude-and fluctuation-based dispersion entropy." 
    Entropy 
    20.3 (2018): 210.

[3] Li Yuxing, Xiang Gao and Long Wang,
    "Reverse dispersion entropy: A new complexity measure for 
    sensor signal." 
    Sensors 
    19.23 (2019): 5203.

[4] Wenlong Fu, et al.,
    "Fault diagnosis for rolling bearings based on fine-sorted 
    dispersion entropy and SVM optimized with mutation SCA-PSO."
    Entropy
    21.4 (2019): 404.
```
