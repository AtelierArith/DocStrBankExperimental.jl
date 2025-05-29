```
MDisp, RDE = MvDispEn(Data)
```

`Data`内のM個の多変量系列に対して、多変量散逸エントロピー推定値（`MDisp`）と逆散逸エントロピー（`RDE`）を返します。デフォルトのパラメータを使用します：埋め込み次元 = 2*ones(M,1)、時間遅延 = ones(M,1)、シンボル数 = 3、アルゴリズムメソッド = "v1"（以下参照）、データ変換 = 正規化累積分布関数（ncdf）対数 = 自然対数、データ正規化 = true、

!!! note
    デフォルトでは、`MvDispEn`は[1]で「mvDEii」と呼ばれるメソッドを使用し、Ahmed & Mandic [2]の元の多変量埋め込みアプローチに従います。したがって、`v1`メソッドは特異なエントロピー推定値を返します。

    `v2`メソッドが選択された場合（`Methodx=="v2"`）、[1]で概説された主なメソッド「mvDE」が適用されます。この場合、エントロピーは長さ1:max(m)の各多変量遅延ベクトルの組み合わせを使用して推定され、各エントロピー値がそれに応じて返されます。詳細については[1]を参照してください。


---

```
MDisp, RDE = MvDispEn(Data::AbstractArray{T,2} where T<:Real; m::Union{AbstractArray{T} where T<:Int, Nothing}=nothing, tau::Union{AbstractArray{T} where T<:Int, Nothing}=nothing, c::Int=3, Methodx::String="v1", Typex::String="NCDF", Norm::Bool=false, Logx::Real=exp(1))
```

指定されたキーワード引数を使用して、`Data`内のM個の多変量データ系列に対して多変量散逸エントロピー推定値（`MDisp`）を返します。

# 引数:

`Data`    - 多変量データセット、N (>10) の観測（行）とM（列）の単変量データ系列のNxM行列

`m`       - 埋め込み次元、M個の正の整数のベクトル

`tau`     - 時間遅延、M個の正の整数のベクトル

`c`       - 変換におけるシンボルの数、1より大きい整数

`Methodx` - [1]で概説された多変量散逸エントロピー推定のメソッド、次のいずれか：

```
    * `"v1"` - Ahmed & Mandic [2]の元の多変量埋め込みアプローチに一致するメソッドを使用し、[1]で「mvDEii」と呼ばれます。（デフォルト）
    * `"v2"` - [1]で導出された主なメソッドを使用し、「mvDE」と呼ばれます。
```

`Typex`   - データからシンボリック系列への変換のタイプ、次のいずれか：

```
            {`'linear'`, `'kmeans'`, `'ncdf'`, `'equal'`}
        これらの変換に関する詳細は`EntropyHub Guide`を参照してください。
```

`Norm`    - `MDisp`と`RDE`値の正規化、ブール値：

```
            * [false]   正規化なし（デフォルト）
            * [true]    可能な散逸パターンの数（`c^m`）に対して正規化します。
```

`Logx`   - 対数の底、正のスカラー 

# 参照   `DispEn`, `DispEn2D`, `MvSampEn`, `MvFuzzEn`, `MvPermEn`, `MSEn`

# 参考文献:

```
[1] H Azami, A Fernández, J Escudero
      "Multivariate Multiscale Dispersion Entropy of Biomedical Times Series"
      Entropy 2019, 21, 913.

[2] Ahmed Mosabber Uddin, Danilo P. Mandic
      "Multivariate multiscale entropy: A tool for complexity
      analysis of multichannel data."
      Physical Review E 84.6 (2011): 061918.

[3] Mostafa Rostaghi and Hamed Azami,
       "Dispersion entropy: A measure for time-series analysis." 
       IEEE Signal Processing Letters 
       23.5 (2016): 610-614.

[4] Hamed Azami and Javier Escudero,
       "Amplitude-and fluctuation-based dispersion entropy." 
       Entropy 
       20.3 (2018): 210.

[5] Li Yuxing, Xiang Gao and Long Wang,
       "Reverse dispersion entropy: A new complexity measure for sensor signal." 
       Sensors 
       19.23 (2019): 5203.
```
