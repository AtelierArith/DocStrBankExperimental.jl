```
EigenAnalysis(proj; [maxdim], [pratio])
```

与えられた射影 `proj` に対する共分散の固有解析。出力の最大次元数 `maxdim` と保持する分散の割合 `pratio` をオプションで指定できます。

## 射影

  * `:V` - 無相関変数（PCA変換）
  * `:VD` - 無相関変数および分散1（DRS変換）
  * `:VDV` - 無相関変数および分散1（SDS変換）

PCA変換で使用される `:V` 射影は、共分散行列の固有ベクトル V にデータを投影します。

DRS変換で使用される `:VD` 射影。`:V` 射影に似ていますが、固有ベクトルは固有値 D の平方逆数で乗算されます。

SDS変換で使用される `:VDV` 射影。`:VD` 変換に似ていますが、データは Vᵀ 行列を使用して元の変数の基底に投影されます。

これらの3つの固有解析のバリアントに関する詳細は、[https://geostatisticslessons.com/lessons/sphereingmaf](https://geostatisticslessons.com/lessons/sphereingmaf) を参照してください。

# 例

```julia
EigenAnalysis(:V)
EigenAnalysis(:VD)
EigenAnalysis(:VDV)
EigenAnalysis(:V, maxdim=3)
EigenAnalysis(:VD, pratio=0.99)
EigenAnalysis(:VDV, maxdim=3, pratio=0.99)
```
