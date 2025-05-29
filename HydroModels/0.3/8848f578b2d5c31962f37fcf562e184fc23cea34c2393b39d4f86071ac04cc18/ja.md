```
@neuralbucket name begin
    fluxes = begin
        ...
    end
    dfluxes = begin
        ...
    end
end
```

指定された名前、fluxes、およびdfluxesを持つHydroBucketを作成します。

# 引数

  * `name`: バケット名のシンボル
  * `fluxes`: HydroFluxまたはNeuralFluxオブジェクトの配列
  * `dfluxes`: StateFluxオブジェクトの配列

# 例

```julia
@hydrobucket :bucket1 begin
    fluxes = [flux1, flux2]
    dfluxes = [dflux1, dflux2]
end
```
