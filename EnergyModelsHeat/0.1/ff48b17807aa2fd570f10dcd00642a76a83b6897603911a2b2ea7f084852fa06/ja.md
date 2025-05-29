```
ResourceHeat{IDT,TS<:TimeProfile,TR<:TimeProfile} <: Resource

ResourceHeat(id, t_supply::TimeProfile, t_return::TimeProfile)
ResourceHeat(id, t_supply::TimeProfile)
ResourceHeat(id, t_supply::Real, t_return::Real)
ResourceHeat(id, t_supply::Real)
```

熱のためのリソースです。

# フィールド

  * **`id::IDT`** はリソースの名前/識別子です。
  * **`t_supply::TS`** は供給温度（°C）を `TimeProfile` として表します。単一の数値を提供すると、`FixedProfile` に変換されます。
  * **`t_return::TR`** は戻り温度（°C）を `TimeProfile` として表します。単一の数値を提供すると、`FixedProfile` に変換されます。このフィールドはオプションであり、値が提供されない場合はゼロに設定されます。
