```
net_radiation!(dest,
              radiation::CoupledRadiativeFluxes,
              model::AbstractModel,
              Y,
              p,
              t)
```

地上でのネット放射フラックスをカップルシミュレーションのために計算します。モデルキャッシュにはフィールド `R_n` が含まれている必要があります。
