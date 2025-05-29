```
RegHydroStor(
    id::Any,
    rate_cap::TimeProfile,
    stor_cap::TimeProfile,
    has_pump::Bool,
    level_init::TimeProfile,
    level_inflow::TimeProfile,
    level_min::TimeProfile,
    opex_var::TimeProfile,
    opex_fixed::TimeProfile,
    stor_res::ResourceCarrier,
    input,
    output,
    Data,
)
```

規制された水力発電ストレージの元のレガシーコンストラクタであり、ポンピング機能の有無にかかわらず使用されます。このバージョンはバージョン0.6.0から廃止され、エラーが発生します。複数のディスパッチの概念を利用するために、[`HydroStor`](@ref)と[`PumpedHydroStor`](@ref)という2つの新しいタイプに置き換えられました。

既存のモデルを新しいモデルに変換する方法に関する詳細情報については、*[ドキュメント](https://energymodelsx.github.io/EnergyModelsRenewableProducers.jl/stable/how-to/update-models/#Adjustments-from-0.4.0-to-0.6.x)*を参照してください。

## フィールド

  * **`id`** はノードの名前/識別子です。
  * **`rate_cap::TimeProfile`** は設置されたレート容量です。
  * **`stor_cap::TimeProfile`** はダムにおける設置されたストレージ容量です。
  * **`has_pump::Bool`** は蓄えられた資源が流入できるかどうかを示します。
  * **`level_init::TimeProfile`** はダムにおける初期蓄積エネルギーです。
  * **`level_inflow::TimeProfile`** は運用期間ごとの電力の流入です。
  * **`level_min::TimeProfile`** は`HydroStorage`ノードに残す必要がある貯水池容量の最小割合です。
  * **`opex_var::TimeProfile`** は生産されたGWhあたりの変動運用費用です。
  * **`opex_fixed::TimeProfile`** はストレージ容量の固定運用コストです。
  * **`stor_res::ResourceCarrier`** は蓄えられた`Resource`です。
  * **`input::Dict{Resource, Real}`** は蓄えられた資源と使用される資源です。Dict内の値はポンプを使用する際のエネルギー損失を示す比率です。
  * **`output::Dict{Resource, Real}`** は蓄えられた資源の1つのエントリのみを含むことができます。
  * **`data::Array{Data}`** 追加データ（例：投資用）。この値はコンストラクタの適用によって条件付きです。
