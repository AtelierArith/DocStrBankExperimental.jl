```
abstract type Crediting
```

Creditingは、ポリシーのために発電機のクレジットレベルを設定するために使用されます。主に[`GenerationStandard`](@ref)sおよび[`ReserveRequirement`](@ref)s（RPS、CES、カーブアウトなど）に使用されます。

## config yaml内のセットアップ

Creditingはyamlファイルで指定されます。タイプキーを指定する必要があり、指定したクレジットタイプに適切なキーも指定する必要があります。以下の設定に2つの例が示されています。

```yaml
base_out_path:    "../out/3bus_rps"
mods:
  example_rps:
    type: "RPS"
    crediting: 
      type: "StandardRPSCrediting"
    gen_filters:
      bus_nation: "archenland"
    load_targets:
      stormness_rps:
        filters:
          state: stormness
        targets:
          y2035: 0.85
          y2040: 0.9
  example_rps_gentype:
    type: "RPS"
    crediting: 
      type: "CreditByGentype"
      credits:
        solar: 0.8
        wind: 1.0
        oswind: 1.0
    gen_filters:
      bus_nation: "narnia"
    load_targets:
      narnia_rps:
        targets:
          y2030: 0.7
          y2035: 0.8
          y2040: 0.9
        filters:  
          nation: "narnia"
  stor:
    type: Storage
    file: "../data/3bus/storage.csv"
```

## 標準クレジットのサブタイプには以下が含まれます：

  * [`CreditByBenchmark`](@ref)
  * [`CreditByGentype`](@ref)

## インターフェースの実装

  * [`get_credit(c::Crediting, data, gen_row::DataFrameRow)`](@ref) - 指定されたCreditingサブタイプの発電機行に対して適切なクレジットレベルを取得します。
