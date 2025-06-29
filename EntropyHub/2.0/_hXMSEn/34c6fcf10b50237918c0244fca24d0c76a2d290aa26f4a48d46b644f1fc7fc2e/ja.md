```
  MSx, Sn, CI = hXMSEn(Sig1, Sig2, Mobj)
```

階層ツリーの各ノードで計算されたクロスエントロピー値のベクトル（`MSx`）、各スケールでのすべてのノードの平均クロスエントロピー値（`Sn`）、およびデータシーケンス`Sig1`と`Sig2`間の階層ツリーの複雑性指数（`CI`）（すなわち、合計`Sn`）を、マルチスケールオブジェクト（`Mobj`）によって指定されたパラメータを使用して3つの時間スケール（デフォルト）で返します。`MSx`のエントロピー値は、ルートノード（S.00）からスケールTのNthサブノード（S.TN）まで順序付けられています：すなわち、S.00、S.10、S.11、S.20、S.21、S.22、S.23、S.30、S.31、S.32、S.33、S.34、S.35、S.36、S.37、S.40、...、S.TN。`Sn`の平均クロスエントロピー値も同様に順序付けられ、ルートノードの値が最初に与えられます：すなわち、S0、S1、S2、...、ST

```
  MSx, Sn, CI = hXMSEn(Sig1::AbstractVector{T} where T<:Real, Sig2::AbstractVector{T} where T<:Real, Mobj::NamedTuple; 
                           Scales::Int=3, RadNew::Int=0, Plotx::Bool=false)
```

階層ツリーの各ノードで計算されたクロスエントロピー値のベクトル（`MSx`）、各スケールでのすべてのノードの平均クロスエントロピー値（`Sn`）、および`Sig1`と`Sig2`に含まれるデータシーケンス間の全階層ツリーの複雑性指数（`CI`）を、以下の名前/値ペア引数を使用して返します：

# 引数：

`Scales`   - 時間スケールの数、整数 > 1（デフォルト：3）                各スケール（T）で、2^(T-1)ノードのエントロピーが推定されます。

`RadNew`   - 半径再スケーリング方法、範囲[1 4]の整数。                `Mobj`によって指定されたエントロピーが`XSampEn`または`XApEn`の場合、                 `RadNew`はツリーの各ノードで半径閾値を更新できるようにします。`Mobj`によって指定された半径値（`r`）がある場合、                これは再スケーリング係数となり、そうでない場合は                0.2（デフォルト）に設定されます。`RadNew`の値は、次のいずれかの方法を指定します：

```
           [1]    プール標準偏差          - r*std(Xt) 

           [2]    プール分散                    - r*var(Xt) 

           [3]    総平均絶対偏差      - r*mean_ad(Xt) 

           [4]    総中央値絶対偏差    - r*med_ad(Xt)
```

`Plotx`    - `Plotx` == trueの場合、各時間スケールでの平均クロスエントロピー                 値のプロット（すなわち、マルチスケールエントロピー曲線）                と、階層ツリー分解における各ノードのエントロピー値を示す階層グラフを返します。  （デフォルト：false）

# 参照：`MSobject`、`XMSEn`、`rXMSEn`、`cXMSEn`、`XSampEn`、`XApEn`、`hMSEn`

# 参考文献：

```
  [1] Matthew W. Flood (2021), 
      "EntropyHub - エントロピック時系列分析のためのオープンソースツールキット"
      PLoS ONE 16(11):e0295448, 
      DOI:  10.1371/journal.pone.0259448
      https://www.EntropyHub.xyz

  [2]   Rui Yan, Zhuo Yang, and Tao Zhang,
      "マルチスケールクロスエントロピー：2つの時系列を分析するための新しいアルゴリズム。" 
      第5回国際自然計算会議。 
      Vol. 1, pp: 411-413 IEEE, 2009。

  [3] Ying Jiang, C-K. Peng and Yuesheng Xu,
      "生物信号のための階層エントロピー分析。"
      計算数学と応用数学のジャーナル
      236.5 (2011): 728-742。
```
