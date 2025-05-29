```julia
BootstrapCrystDistributionKDE(smpl::ChronAgeData; cutoff=-0.05, [tpbloss=0])
```

Chron.ChronAgeDataオブジェクトから、いくつかのサンプルのデータを含む前噴出（または前堆積）鉱物結晶化分布の形状の推定をブートストラップし、スタックされたサンプルデータのカーネル密度推定を使用します。

`smpl.Path`にcsvファイルとして提供されたサンプルがU-Pb同位体データファイルの5列形式を取る場合、年齢と不確実性は、オプションで`tpbloss`として指定されたPb損失の時間に基づく上部交点のものになります。

不確実性は、`smpl.inputSigmaLevel`の値に基づいて、1シグマまたは2シグマの絶対値として扱われます。

### 例

```julia
BootstrappedDistribution = BootstrapCrystDistributionKDE(smpl)
```
