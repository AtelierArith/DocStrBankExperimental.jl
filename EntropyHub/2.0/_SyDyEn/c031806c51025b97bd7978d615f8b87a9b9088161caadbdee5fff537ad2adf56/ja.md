```
  SyDy, Zt = SyDyEn(Sig)
```

データシーケンス（`Sig`）の記号動的エントロピー（`SyDy`）と記号シーケンス（`Zt`）をデフォルトのパラメータを使用して返します：埋め込み次元 = 2、時間遅延 = 1、シンボル = 3、対数 = 自然、記号的分割タイプ = 最大エントロピー分割（`MEP`）、正規化 = 可能なベクトルの順列に対して正規化（c^m）

```
  SyDy, Zt = SyDyEn(Sig::AbstractArray{T,1} where T<:Real; m::Int=2, tau::Int=1, c::Int=3, Typex::String="MEP", Logx::Real=exp(1), Norm::Bool=true)
```

指定された「キーワード」引数を使用してデータシーケンス（`Sig`）の記号動的エントロピー（`SyDy`）と記号シーケンス（`Zt`）を返します：

# 引数：

`m`     - 埋め込み次元、正の整数  

`tau`   - 時間遅延、正の整数  

`c`     - シンボルの数、1より大きい整数  

`Typex` - 記号シーケンスの分割方法のタイプ、次のいずれか：  

```
        {"linear","uniform","MEP"(デフォルト),"kmeans"}
```

`Logx`  - 対数の底、正のスカラー    

`Norm`  - SyDyEn値の正規化： 

```
        [false]  正規化なし 
        [true]   可能なベクトルの順列に対して正規化（c^m+1） - デフォルト
```

これらのパラメータに関する詳細はEntropyHubガイドを参照してください。

# 参照：`DispEn`、`PermEn`、`CondEn`、`SampEn`、`MSEn`

# 参考文献：

```
  [1] Yongbo Li, et al.,
      "A fault diagnosis scheme for planetary gearboxes using 
      modified multi-scale symbolic dynamic entropy and mRMR feature 
      selection." 
      Mechanical Systems and Signal Processing 
      91 (2017): 295-312. 

  [2] Jian Wang, et al.,
      "Fault feature extraction for multiple electrical faults of 
      aviation electro-mechanical actuator based on symbolic dynamics
      entropy." 
      IEEE International Conference on Signal Processing, 
      Communications and Computing (ICSPCC), 2015.

  [3] Venkatesh Rajagopalan and Asok Ray,
      "Symbolic time series analysis via wavelet-based partitioning."
      Signal processing 
      86.11 (2006): 3309-3320.
```
