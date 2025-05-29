```
ClimaLand.get_drivers(model::RichardsModel)
```

RichardsModelのドライバ変数シンボルを返します。これらは境界条件のタイプに依存し、現在は指定された時間および空間変動の降水量によって駆動されるRichardsAtmosDrivenFluxBCにのみ必要です。
