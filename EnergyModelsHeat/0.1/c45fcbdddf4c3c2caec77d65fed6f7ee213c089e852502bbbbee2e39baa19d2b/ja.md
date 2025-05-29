```
HeatPump <: EMB.NetworkNode
```

`HeatPump`ノードは、エネルギー駆動力（*例*、電気）を利用して低温熱を高温熱に変換します。

# フィールド

  * **`id`** はノードの名前/識別子です。
  * **`cap::TimeProfile`** は設置された加熱能力です。
  * **`cap_lower_bound`** は、[0, 1]の範囲内での柔軟性を反映した最低能力の下限です。
  * **`t_source`** は熱源の温度プロファイルです。
  * **`t_sink`** はコンデンサーのシンク温度です。温度は°Cで指定する必要があります。
  * **`eff_carnot`** はカルノー効率COP*real/COP*carnotです。値は[0, 1]の範囲内でなければなりません。
  * **`input_heat`** は低温熱入力のリソースです。
  * **`driving_force`** は駆動力のリソースです（*例*、電気）。
  * **`opex_var::TimeProfile`** は生産されたエネルギー単位あたりの変動運営費です。
  * **`opex_fixed::TimeProfile`** は固定運営費です。
  * **`output::Dict{<:Resource, <:Real}`** は変換値`Real`を持つ生産された[`Resource`](@extref EnergyModelsBase.Resource)です。
  * **`data::Vector{<:Data}`** は追加データ（*例*、投資用）です。フィールド`data`はコンストラクタの使用によって条件付きです。
