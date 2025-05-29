```
 ClimaLand.make_update_aux(canopy::CanopyModel{FT,
                                              <:AutotrophicRespirationModel,
                                              <:Union{BeerLambertModel, TwoStreamModel},
                                              <:FarquharModel,
                                              <:MedlynConductanceModel,
                                              <:PlantHydraulicsModel,},
                          ) where {FT}
```

`CanopyModel`のための`update_aux!`関数を作成します。これは、キャノピーモデルのコンポーネントがパラメトリック型シグネチャのタイプである場合に特化した`update_aux!`のメソッドです：`AutotrophicRespirationModel`、`AbstractRadiationModel`、`FarquharModel`、`MedlynConductanceModel`、および`PlantHydraulicsModel`。

植物の水理モデルには、予測的な`compute_exp_tendency!`関数で更新される補助変数があります。混乱を招くかもしれませんが、これは状態ベクトルを複数回ループするのを避けるため、パフォーマンスの向上に寄与します。

他のサブコンポーネントは互いに大きく依存しているため、これらのサブコンポーネントを持つ`CanopyModel`のバージョンには、ここに示すように単一の`update_aux!`関数があります。
