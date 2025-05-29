```
MSx, CI = MvMSEn(Data, Mobj)
```

`Data`内のデータ系列の多変量マルチスケールエントロピー値のベクトル（`MSx`）と複雑性指数（`CI`）を、マルチスケールオブジェクト（`Mobj`）によって指定されたパラメータを使用して、粗いグレイニング（デフォルト）で3つの時間スケールにわたって返します。

!!! note
    デフォルトでは、`MvSampEn`および`MvFuzzEn`の多変量エントロピーアルゴリズムは、[1]で適用される埋め込み空間のすべての可能な`m+1`拡張にわたって遅延ベクトルを比較することによって、エントロピー値を「完全」な方法で推定します。これらの方法は、ほとんどのエントロピーアルゴリズムのように0に下限されていないため、基底の多変量エントロピー関数が`MvSampEn`および`MvFuzzEn`である場合、確率過程に対しても`MvMSEn`が負のエントロピー値を返す可能性があります...


---

```
MSx, CI = MSEn(Data::AbstractArray{T,2} where T<:Real, Mobj::NamedTuple; Scales::Int=3, Methodx::String="coarse", Plotx::Bool=false)
```

`Data`内のデータ系列の多変量マルチスケールエントロピー値のベクトル（`MSx`）と複雑性指数（`CI`）を、マルチスケールオブジェクト（`Mobj`）によって指定されたパラメータと以下のキーワード引数を使用して返します。

# 引数:

`Scales`   - 時間スケールの数、1より大きい整数（デフォルト: 3）

`Method`   - グレイニング方法、次のいずれか:

```
          {`coarse`,`modified`,`generalized`} [default = `coarse`]  
          これらのグレイニング手順の詳細については、EntropyHubガイドを参照してください。
```

`Plotx`    - Plotx == true の場合、各時間スケールでのエントロピー値のプロット（すなわち、マルチスケールエントロピー曲線）を返します [デフォルト: false]

!!! tip
    これらのグレイニング手順の詳細については、EntropyHubガイドを参照してください。


# 参照: `MSobject`, `cMvMSEn`, `MvFuzzEn`, `MvSampEn`, `MvPermEn`, `MvCoSiEn`, `MvDispEn`

# 参考文献:

```
[1] Ahmed Mosabber Uddin, Danilo P. Mandic
     "Multivariate multiscale entropy analysis."
     IEEE signal processing letters 19.2 (2011): 91-94.

[2] Madalena Costa, Ary Goldberger, and C-K. Peng,
     "Multiscale entropy analysis of complex physiologic time series."
     Physical review letters
     89.6 (2002): 068102.

[3] Vadim V. Nikulin, and Tom Brismar,
     "Comment on “Multiscale entropy analysis of complex physiologic
     time series”." 
     Physical Review Letters 
     92.8 (2004): 089803.

[4] Madalena Costa, Ary L. Goldberger, and C-K. Peng. 
     "Costa, Goldberger, and Peng reply." 
     Physical Review Letters
     92.8 (2004): 089804.

[5] Madalena Costa, Ary L. Goldberger and C-K. Peng,
     "Multiscale entropy analysis of biological signals." 
     Physical review E 
     71.2 (2005): 021906.

[6] Ranjit A. Thuraisingham and Georg A. Gottwald,
     "On multiscale entropy analysis for physiological data."
     Physica A: Statistical Mechanics and its Applications
     366 (2006): 323-332.

[7] Ahmed Mosabber Uddin, Danilo P. Mandic
     "Multivariate multiscale entropy: A tool for complexity
     analysis of multichannel data."
     Physical Review E 84.6 (2011): 061918.
```
