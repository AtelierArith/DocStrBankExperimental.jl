```
MSx, CI = cXMSEn(Sig1, Sig2, Mobj)
```

`Sig1` と `Sig2` に含まれる2つの単変量データ系列間の複合マルチスケール交差エントロピー値のベクトル（`MSx`）を、マルチスケールオブジェクト（`Mobj`）によって指定されたパラメータを使用して、3つの時間スケールにわたる複合マルチスケール法（cMSE）を使用して返します。

```
MSx, CI = cXMSEn(Sig1::AbstractVector{T} where T<:Real, Sig2::AbstractVector{T} where T<:Real, Mobj::NamedTuple; 
                      Scales::Int=3, RadNew::Int=0, Refined::Bool=false, Plotx::Bool=false)
```

`Sig1` と `Sig2` に含まれるデータ系列間の複合マルチスケール交差エントロピー値のベクトル（`MSx`）を、マルチスケールオブジェクト（`Mobj`）によって指定されたパラメータと以下のキーワード引数を使用して返します。

# 引数:

`Scales`   - 時間スケールの数、1より大きい整数（デフォルト: 3）

`RadNew`   - 半径再スケーリング法、範囲 [1 4] の整数。              `Mobj` によって指定されたエントロピーが `XSampEn` または `XApEn` の場合、               RadNew は各時間スケールでの部分系列の半径閾値              (Ykj) を再スケーリングします。`Mobj` によって指定された半径値              (`r`) がある場合、これが再スケーリング係数となり、              そうでない場合は0.2（デフォルト）に設定されます。RadNewの値は              次のいずれかの方法を指定します:

```
         [1]    プール標準偏差          - r*std(Ykj)

         [2]    プール分散                    - r*var(Ykj)

         [3]    総平均絶対偏差      - r*mean_ad(Ykj)

         [4]    総中央値絶対偏差    - r*med_ad(Ykj,1)
```

`Refined`  - 洗練された複合 XMSEn メソッド。`Refined` が true の場合、               `Mobj` によって指定されたエントロピー関数が `XSampEn` または `XFuzzEn` の場合、cXMSEn              は洗練された複合マルチスケールエントロピー (rcXMSEn) を返します。              （デフォルト: false） `Plotx`    - `Plotx` が true の場合、各               時間スケールでのエントロピー値のプロットを返します               （すなわち、マルチスケールエントロピー曲線） [デフォルト: false]

# 参照: `MSobject`, `XMSEn`, `rXMSEn`, `hXMSEn`, `XSampEn`, `XApEn`, `cMSEn`

# 参考文献:

```
[1] Rui Yan, Zhuo Yang, and Tao Zhang,
    "Multiscale cross entropy: a novel algorithm for analyzing two
    time series." 
    5th International Conference on Natural Computation. 
    Vol. 1, pp: 411-413 IEEE, 2009.

[2] Yi Yin, Pengjian Shang, and Guochen Feng, 
    "Modified multiscale cross-sample entropy for complex time 
    series."
    Applied Mathematics and Computation 
    289 (2016): 98-110.

[3] Madalena Costa, Ary Goldberger, and C-K. Peng,
    "Multiscale entropy analysis of complex physiologic time series."
    Physical review letters
    89.6 (2002): 068102.

[4] Antoine Jamin, et al,
    "A novel multiscale cross-entropy method applied to navigation 
    data acquired with a bike simulator." 
    41st annual international conference of the IEEE EMBC
    IEEE, 2019.

[5] Antoine Jamin and Anne Humeau-Heurtier. 
    "(Multiscale) Cross-Entropy Methods: A Review." 
    Entropy 
    22.1 (2020): 45.

[6] Shuen-De Wu, et al.,
    "Time series analysis using composite multiscale entropy." 
    Entropy 
    15.3 (2013): 1069-1084.
```
