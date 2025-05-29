```julia
BootstrapCrystDistributionKDE(data::AbstractArray, [sigma::AbstractArray]; cutoff=-0.05)
```

1次元または2次元のサンプル年齢の配列（サンプルごとに1行、データごとに1列、必要に応じてNaNでパディング）と同等のサイズの1シグマ不確実性の配列から、前噴火（または前堆積）鉱物結晶化分布の形状の推定をブートストラップし、スタックされたサンプルデータのカーネル密度推定を使用します。

### 例

```julia
# 年齢が[1,2,3,...10] Maで不確実性がそれぞれ1 Maの合成データセットのための
# 結晶化分布をブートストラップ
BootstrappedDistribution = BootstrapCrystDistributionKDE(1:10, ones(10))
```
