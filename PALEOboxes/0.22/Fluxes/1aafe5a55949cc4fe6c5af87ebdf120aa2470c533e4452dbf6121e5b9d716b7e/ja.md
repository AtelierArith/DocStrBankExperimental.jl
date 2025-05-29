```
フラックス
```

ターゲットおよび寄与変数のコレクションを作成および管理し、ドメイン内またはドメイン間のフラックスを定義します。

# ドメイン内の生物地球化学的フラックスを定義するための規約

  * ストイキオメトリー Corg:N:P:Ccarb を持つ粒子状有機物（CaCO3を含む）は通常、次のように転送されます: `flux_list` `["P", "N", "Corg::CIsotope", "Ccarb::CIsotope"]` で、関数を示すプレフィックス（例: `export_`）が付けられます。
  * 溶質フラックスは通常、次のように転送されます: `flux_list`  `["DIC::CIsotope", "TAlk", "Ca", "P", "O2", "SO4::SIsotope", "H2S::SIsotope", "CH4::CIsotope"]` （これらの名前は溶質のための貯蔵庫名と一致します）で、関数を示すプレフィックス（通常は `flux_` または `soluteflux_`）が付けられます。

# モジュール間のグローバルフラックスを定義するための規約

モデル構成 `.yaml` ファイルは、各グローバルフラックスのために `Domain` を作成し、1つ以上の [`Fluxes.ReactionFluxTarget`](@ref) を含む必要があります。フラックスは、その後、各宛先ドメインに [`Fluxes.ReactionFluxTransfer`](@ref) を追加することによって転送（コピー）されます。

地球システムフラックスの命名規約:

| ドメイン名                 | ターゲットプレフィックス     | flux_list (例示、必要に応じて追加)                                                                              |
|:--------------------- |:---------------- |:---------------------------------------------------------------------------------------------------- |
| fluxAtoLand           | flux_            | ["CO2::CIsotope", "O2"]                                                                              |
| fluxRtoOcean          | flux_            | ["DIC::CIsotope", "TAlk", "Ca", "P", "SO4::SIsotope"]                                                |
| fluxOceanBurial       | flux_            | ["Corg::CIsotope", "Ccarb::CIsotope", "Porg", "Pauth", "PFe", "P", "GYP::SIsotope", "PYR::SIsotope"] |
| fluxSedCrusttoAOcean  | flux_            | ["C::CIsotope", "S::SIsotope", "Redox"]                                                              |
| fluxLandtoSedCrust    | flux_            | ["Ccarb::CIsotope", "Corg::CIsotope", "GYP::SIsotope", "PYR::SIsotope"]                              |
| fluxOceanfloor        | particulateflux_ | ["P", "N", "Corg::CIsotope", "Ccarb::CIsotope"]                                                      |
|                       | soluteflux_      | ["DIC::CIsotope", "TAlk", "Ca", "P", "O2", "SO4::SIsotope", "H2S::SIsotope", "CH4::CIsotope"]        |
| fluxAtmtoOceansurface | flux_            | ["CO2::CIsotope", "CH4::CIsotope", "O2"]                                                             |
