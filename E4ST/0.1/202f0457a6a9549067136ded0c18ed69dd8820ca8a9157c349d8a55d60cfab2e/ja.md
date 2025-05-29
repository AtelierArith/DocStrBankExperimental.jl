```
const RPS = GenerationStandard{:RPS}
```

**再生可能ポートフォリオ基準** - 特定の地域からの負荷の一定量を、適格なクリーン/再生可能エネルギーによって供給することを制約する政策。

RPSは、デフォルトのクレジットタイプがStandardRPSCreditingであるGenerationStandardのエイリアスとして定義されています。RPSのmod_rankは1.0で、これはGenerationStandardsのランクです。

## フィールド

  * `name` - 政策の名前
  * `targets` - RPSの年間目標
  * `crediting` - クレジット構造および関連フィールド。標準CESクレジットはCreditingByBenchmarkです。
  * `gen_filters` - RPSを満たすために適格な発電をフィルタリングします。時には、適格な発電機がRPS負荷地域の外にある場合もあります。
  * `load_bus_filters` - RPS負荷地域に該当するバスをフィルタリングします。RPSはこれらのバスからの負荷に適用されます。

[`GenerationStandard`](@ref)
