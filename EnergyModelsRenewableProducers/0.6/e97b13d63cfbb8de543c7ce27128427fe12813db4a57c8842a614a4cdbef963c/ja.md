```
HydroStor(
    id::Any,
    rate_cap::TimeProfile,
    stor_cap::TimeProfile,
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

ポンプ機能のない規制された水力発電所のためのレガシーコンストラクタ。このバージョンは近い将来廃止され、新しいバージョンの `HydroStor{StorageBehavior}` に置き換えられます。この新しいバージョンでは、パラメトリック入力が水力発電所の動作を定義します。さらに、`AbstractStorageParameters` の導入により、ストレージの `level` と `discharge` 容量に対する個々の容量とOPEXの寄与を改善した説明が可能になります。

既存のモデルを新しいモデルに変換する方法についての詳細は、*[ドキュメント](https://energymodelsx.github.io/EnergyModelsRenewableProducers.jl/stable/how-to/update-models/#Adjustments-from-0.4.0-to-0.6.x)*を参照してください。

## フィールド

  * **`id`** はノードの名前/識別子です。
  * **`rate_cap::TimeProfile`** は設置されたレート容量です。
  * **`stor_cap::TimeProfile`** はダムにおける設置されたストレージ容量です。
  * **`level_init::TimeProfile`** はダムにおける初期蓄積エネルギーです。
  * **`level_inflow::TimeProfile`** は運用期間ごとの電力の流入です。
  * **`level_min::TimeProfile`** は `HydroStorage` ノードに残さなければならない貯水池容量の最小割合です。
  * **`opex_var::TimeProfile`** は生産されたGWhあたりの変動運用費用です。
  * **`opex_fixed::TimeProfile`** はストレージ容量の固定運用コストです。
  * **`stor_res::ResourceCarrier`** は蓄積された `Resource` です。
  * **`input::Dict{Resource, Real}`** は蓄積され使用されるリソースです。Dict内の値はポンプを使用する際のエネルギー損失を示す比率です。
  * **`output::Dict{Resource, Real}`** は蓄積されたリソースの1つのエントリのみを含むことができます。
  * **`data::Array{Data}`** 追加データ（例：投資用）。この値はコンストラクタの適用によって条件付きです。
