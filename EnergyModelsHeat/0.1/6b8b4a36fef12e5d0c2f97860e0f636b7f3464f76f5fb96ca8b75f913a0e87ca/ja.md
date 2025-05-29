```
ThermalEnergyStorage{T} <: Storage{T}
```

`ThermalEnergyStorage`は、主に[`RefStorage`](@extref EnergyModelsBase.RefStorage)のように機能しますが、熱エネルギー損失を含めるオプションが追加されています。熱損失は、前の時間帯のストレージレベルに対する失われる熱エネルギーの量を説明する熱損失係数を通じて定量化されます。

[`RefStorage`](@extref EnergyModelsBase.RefStorage)との主な違いは、これらの熱損失が充電または放電中には発生しないことです。すなわち、熱損失はストレージレベルに比例します。

!!! warning "StorageBehavior"
    現在の実装の`ThermalEnergyStorage`は、ストレージ動作として[`CyclicRepresentative`](@extref EnergyModelsBase.CyclicRepresentative)のみをサポートしています。この入力は、内部コンストラクタの利用により必須ではありません。


# フィールド

  * **`id`** はノードの名前/識別子です。
  * **`charge::AbstractStorageParameters`** は`ThermalEnergyStorage`ノードの充電パラメータです。選択したタイプに応じて、充電パラメータには変動OPEX、固定OPEX、および/または容量が含まれる場合があります。
  * **`level::AbstractStorageParameters`** は`ThermalEnergyStorage`のレベルパラメータです。選択したタイプに応じて、充電パラメータには変動OPEXおよび/または固定OPEXが含まれる場合があります。
  * **`stor_res::Resource`** は保存された[`Resource`](@extref EnergyModelsBase.Resource)です。
  * **`heat_loss_factor::Float64`** は相対的な熱損失のパーセントです。
  * **`input::Dict{<:Resource,<:Real}`** は変換値`Real`を持つ入力[`Resource`](@extref EnergyModelsBase.Resource)です。
  * **`output::Dict{<:Resource,<:Real}`** は変換値`Real`を持つ生成された[`Resource`](@extref EnergyModelsBase.Resource)です。リンクおよび保存された[`Resource`](@extref EnergyModelsBase.Resource)にのみ関連し、出力値は計算に利用されません。
  * **`data::Vector{<:Data}`** は追加データ（*例*、投資用）です。フィールド`data`はコンストラクタの使用によって条件付きです。
