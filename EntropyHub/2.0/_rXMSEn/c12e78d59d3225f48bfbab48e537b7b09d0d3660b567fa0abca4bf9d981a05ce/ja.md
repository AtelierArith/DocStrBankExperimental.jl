```
  MSx, CI = rXMSEn(Sig1, Sig2, Mobj)
```

`Sig1` と `Sig2` に含まれるデータ系列間の洗練されたマルチスケール交差エントロピー値のベクトル (`MSx`) と複雑性指数 (`CI`) を返します。これは、マルチスケールオブジェクト (`Mobj`) によって指定されたパラメータと、次のデフォルトパラメータを使用します: スケール = 3、バターワースLPFの次数 = 6、スケール (T) におけるバターワースLPFのカットオフ周波数: Fc = 0.5/T。`Mobj` によって指定されたエントロピー関数が `XSampEn` または `XApEn` の場合、`rMSEn` は、`Mobj` によって `r` 値が提供されていないときに、各スケールでデータ系列 (Xt) の閾値半径を 0.2*SDpooled(Xa, Xb) に更新します。`r` が指定されている場合は、`r`*SDpooled(Xa, Xb) になります。

```
  MSx, CI = rXMSEn(Sig1::AbstractVector{T} where T<:Real, Sig2::AbstractVector{T} where T<:Real, Mobj::NamedTuple;
                   Scales::Int=3, F_Order::Int=6, F_Num::Float64=0.5, RadNew::Int=0, Plotx::Bool=false)
```

`Sig1` と `Sig2` に含まれるデータ系列間の洗練されたマルチスケール交差エントロピー値のベクトル (`MSx`) と複雑性指数 (`CI`) を返します。これは、マルチスケールオブジェクト (`Mobj`) によって指定されたパラメータと、次のキーワード引数を使用します:

# 引数:

`Scales`   - 時間スケールの数、1より大きい整数 (デフォルト: 3)  

`F_Order`  - バターワースローパスフィルタの次数、正の整数 (デフォルト: 6)  

`F_Num`    - バターワースローパスフィルタのカットオフ周波数の分子、                スカラー値の範囲 [0 < `F_Num` < 1]。各スケール (T) におけるカットオフ周波数は: Fc = `F_Num`/T になります。 (デフォルト: 0.5) 

`RadNew`   - 半径再スケーリング方法、範囲 [1 4] の整数。                `Mobj` によって指定されたエントロピーが `XSampEn` または `XApEn` の場合、                 `RadNew` は各時間スケール (Xt) で半径閾値を更新できるようにします。`Mobj` によって半径値 (`r`) が指定されている場合、これは再スケーリング係数になります。そうでない場合は 0.2 に設定されます (デフォルト)。`RadNew` の値は次のいずれかの方法を指定します: 

```
           [1]    プール標準偏差          - r*std(Xt) 

           [2]    プール分散                    - r*var(Xt) 

           [3]    総平均絶対偏差      - r*mean_ad(Xt) 

           [4]    総中央値絶対偏差    - r*med_ad(Xt)
```

`Plotx`    - `Plotx` == true の場合、各時間スケールでのエントロピー値のプロットを返します                 (すなわち、マルチスケールエントロピー曲線)                [デフォルト = false] 

# 参照: `MSobject`, `XMSEn`, `cXMSEn`, `hXMSEn`, `XSampEn`, `XApEn`, `MSEn`

# 参考文献:

```
  [1] Matthew W. Flood (2021), 
      "EntropyHub - An open source toolkit for entropic time series analysis"
      PLoS ONE 16(11):e0295448, 
      DOI:  10.1371/journal.pone.0259448
      https://www.EntropyHub.xyz

  [2]   Rui Yan, Zhuo Yang, and Tao Zhang,
      "Multiscale cross entropy: a novel algorithm for analyzing two
      time series." 
      5th International Conference on Natural Computation. 
      Vol. 1, pp: 411-413 IEEE, 2009.

  [3] José Fernando Valencia, et al.,
      "Refined multiscale entropy: Application to 24-h holter 
      recordings of heart period variability in healthy and aortic 
      stenosis subjects." 
      IEEE Transactions on Biomedical Engineering 
      56.9 (2009): 2202-2213.

  [4] Puneeta Marwaha and Ramesh Kumar Sunkaria,
      "Optimal selection of threshold value ‘r’for refined multiscale
      entropy." 
      Cardiovascular engineering and technology 
      6.4 (2015): 557-576.

  [5] Yi Yin, Pengjian Shang, and Guochen Feng, 
      "Modified multiscale cross-sample entropy for complex time 
      series."
      Applied Mathematics and Computation 
      289 (2016): 98-110.

  [6] Antoine Jamin, et al,
      "A novel multiscale cross-entropy method applied to navigation 
      data acquired with a bike simulator." 
      41st annual international conference of the IEEE EMBC
      IEEE, 2019.

  [7] Antoine Jamin and Anne Humeau-Heurtier. 
      "(Multiscale) Cross-Entropy Methods: A Review." 
      Entropy 
      22.1 (2020): 45.
```
