```
MSx, CI = XMSEn(Sig1, Sig2, Mobj)
```

`Sig1` と `Sig2` に含まれるデータ系列間の多スケール交差エントロピー値のベクトル `MSx` と複雑性指標 `CI` を、3つの時間スケールで `Mobj` によって指定されたパラメータを使用して返します。粗粒化は `default` です。

```
MSx,CI = MSEn(Sig1::AbstractVector{T} where T<:Real, Sig2::AbstractVector{T} where T<:Real, Mobj::NamedTuple; 
                 Scales::Int=3, Methodx::String="coarse", RadNew::Int=0, Plotx::Bool=false)
```

`Sig1` と `Sig2` に含まれるデータ系列の多スケール交差エントロピー値のベクトル `MSx` と複雑性指標 `CI` を、`Mobj` によって指定されたパラメータと以下の 'キーワード' 引数を使用して返します。

# 引数:

`Scales`   - 時間スケールの数、整数 > 1   (デフォルト: 3) 

`Method`   - 粗粒化方法、次のいずれか:

```
         {`"coarse", "modified", "imf", "timeshift","generalized"`}  [デフォルト: 'coarse'] 
         粗粒化手順の詳細については、Entropyhub ガイドを参照してください。
```

`RadNew`   - 半径再スケーリング方法、範囲 [1 4] の整数。              `Mobj` によって指定されたエントロピーが `XSampEn` または `XApEn` の場合、               `RadNew` は各時間スケール (Xt) で半径閾値を更新できるようにします。もし `Mobj` によって指定された半径値 (`r`) がある場合、              これは再スケーリング係数となり、そうでない場合は              0.2 (デフォルト) に設定されます。`RadNew` の値は次のいずれかの方法を指定します: 

```
         [1]    プール標準偏差          - r*std(Xt) 

         [2]    プール分散                    - r*var(Xt) 

         [3]    総平均絶対偏差      - r*mean_ad(Xt) 

         [4]    総中央値絶対偏差    - r*med_ad(Xt)
```

`Plotx`    - `Plotx` が true の場合、各時間スケールでのエントロピー値のプロットを返します              (すなわち、多スケールエントロピー曲線)  [デフォルト: false]

`これらの粗粒化手順の詳細については、EntropyHub ガイドを参照してください。`

# 参照: `MSobject`, `MSEn`, `cXMSEn`, `rXMSEn`, `hXMSEn`, `XSampEn`, `XApEn`, `XFuzzEn`

# 参考文献:

```
[1] Rui Yan, Zhuo Yang, and Tao Zhang,
    "Multiscale cross entropy: a novel algorithm for analyzing two
    time series." 
    5th International Conference on Natural Computation. 
    Vol. 1, pp: 411-413 IEEE, 2009.

[2] Madalena Costa, Ary Goldberger, and C-K. Peng,
    "Multiscale entropy analysis of complex physiologic time series."
    Physical review letters
    89.6 (2002): 068102.

[3] Vadim V. Nikulin, and Tom Brismar,
    "Comment on “Multiscale entropy analysis of complex physiologic
    time series”." 
    Physical review letters 
    92.8 (2004): 089803.

[4] Madalena Costa, Ary L. Goldberger, and C-K. Peng. 
    "Costa, Goldberger, and Peng reply." 
    Physical Review Letters
    92.8 (2004): 089804.

[5] Antoine Jamin, et al,
    "A novel multiscale cross-entropy method applied to navigation 
    data acquired with a bike simulator." 
    41st annual international conference of the IEEE EMBC
    IEEE, 2019.

[6] Antoine Jamin and Anne Humeau-Heurtier. 
    "(Multiscale) Cross-Entropy Methods: A Review." 
    Entropy 
    22.1 (2020): 45.
```
