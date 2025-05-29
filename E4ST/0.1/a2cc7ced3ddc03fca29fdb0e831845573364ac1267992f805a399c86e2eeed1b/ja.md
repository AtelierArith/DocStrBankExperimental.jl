```
const CES = GenerationStandard{:CES}
```

**クリーンエネルギー基準** - 負荷供給主体が一定量のクリーンエネルギークレジットを購入しなければならない政策。発電の種類に対するクレジットの数は、通常、ベンチマークに対する排出率に依存します。

CESは[`GenerationStandard`](@ref)のエイリアスとして定義されています。

デフォルトのクレジット付与は指定されていませんが、標準的なクレジット付与は[`CreditByBenchmark`](@ref)であり、ベンチマークは設定で指定する必要があります。

## フィールド

  * `name` - 政策の名前
  * `targets` - CESの年間目標
  * `crediting` - クレジット付与の構造と関連フィールド。CESのクレジット付与はしばしば[`CreditByBenchmark`](@ref)です。
  * `gen_filters` - CESを満たすために適格な発電に関するフィルター。時には、適格な発電機がRPS負荷地域の外にある場合もあります。
  * `load_bus_filters` - 負荷地域に該当するバスに関するフィルター。CESはこれらのバスからの負荷に適用されます。

[`GenerationStandard`](@ref)
