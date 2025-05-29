```
MSx, CI = cMvMSEn(Data, Mobj)
```

データシーケンス `Data` の複合多変量マルチスケールエントロピー値のベクトル（`MSx`）と複雑性指数（`CI`）を、マルチスケールオブジェクト（`Mobj`）によって指定されたパラメータを使用して、粗視化（デフォルト）で3つの時間スケールにわたって返します。

!!! note
    デフォルトでは、`MvSampEn` および `MvFuzzEn` の多変量エントロピーアルゴリズムは、[1] で適用される埋め込み空間のすべての可能な `m+1` 拡張にわたって遅延ベクトルを比較することによって、エントロピー値を「フル」メソッドを使用して推定します。これらのメソッドは、ほとんどのエントロピーアルゴリズムのように0に下限されていないため、基底の多変量エントロピー関数が `MvSampEn` および `MvFuzzEn` の場合、`MvMSEn` は確率過程に対しても負のエントロピー値を返す可能性があります...


---

```
MSx, CI = cMvMSEn(Data, Mobj, Refined = True)
```

データシーケンス（`Data`）のための洗練された複合マルチスケールエントロピー値のベクトル（`MSx`）を、洗練された複合多変量マルチスケールエントロピー法（rcMSE）を使用して、マルチスケールオブジェクト（`Mobj`）によって指定されたパラメータを使用して、3つの時間スケールにわたって返します。`Refined == true` の場合、基底エントロピー法は `MvSampEn` または `MvFuzzEn` でなければなりません。エントロピー法が `MvSampEn` の場合、cMvMSEn は [1] で説明されている方法を採用します。エントロピー法が `MvFuzzEn` の場合、cMvMSEn は [5] で説明されている方法を採用します。

```
MSx, CI = cMVMSEn(Data::AbstractArray{T,2} where T<:Real, Mobj::NamedTuple; Scales::Int=3, Refined::Bool="false", Plotx::Bool=false)
```

データシーケンス `Data` の多変量マルチスケールエントロピー値のベクトル（`MSx`）と複雑性指数（`CI`）を、マルチスケールオブジェクト（`Mobj`）によって指定されたパラメータと以下のキーワード引数を使用して返します。

# 引数:

`Scales`   - 時間スケールの数、整数 > 1   （デフォルト: 3）

`Refined`  - 洗練された複合 MvMSEn メソッド。`Refined == True` で、`Mobj` によって指定されたエントロピー関数が `MvSampEn` または `MvFuzzEn` の場合、`cMvMSEn` は洗練された複合多変量マルチスケールエントロピー（rcMSEn）を返します（デフォルト: False）

`Plotx`    - Plotx == true の場合、各時間スケールでのエントロピー値のプロットを返します（すなわち、マルチスケールエントロピー曲線）[デフォルト: false]

# 参照: `MvMSEn`, `MSobject`, `MvFuzzEn`, `MvSampEn`, `MvPermEn`, `MvCoSiEn`, `MvDispEn`

# 参考文献:

```
[1] Shuen-De Wu, et al.,
    "Time series analysis using composite multiscale entropy."
    Entropy
    15.3 (2013): 1069-1084.

[2] Shuen-De Wu, et al.,
    "Analysis of complex time series using refined composite
    multiscale entropy."
    Physics Letters A
    378.20 (2014): 1369-1374.

[3] Ahmed Mosabber Uddin, Danilo P. Mandic
    "Multivariate multiscale entropy: A tool for complexity
    analysis of multichannel data."
    Physical Review E 84.6 (2011): 061918.

[4] Ahmed Mosabber Uddin, Danilo P. Mandic
    "Multivariate multiscale entropy analysis."
    IEEE signal processing letters 19.2 (2011): 91-94.

[5] Azami, Alberto Fernández, Javier Escudero.
    "Refined multiscale fuzzy entropy based on standard deviation for
    biomedical signal analysis."
    Medical & biological engineering & computing 55 (2017): 2037-2052.
```
