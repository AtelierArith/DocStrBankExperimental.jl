```
Specification{F <: Property}
```

仕様は、満足モードと戦略モードを伴うプロパティです。満足モードは `Optimistic` または `Pessimistic` のいずれかです。詳細については [`SatisfactionMode`](@ref) を参照してください。戦略モードは `Maxmize` または `Minimize` のいずれかです。詳細については [`StrategyMode`](@ref) を参照してください。

### フィールド

  * `prop::F`: 検証プロパティ（時間論理または到達可能性のようなもの）。
  * `satisfaction::SatisfactionMode`: 満足モード（楽観的または悲観的のいずれか）。デフォルトは悲観的です。
  * `strategy::StrategyMode`: 戦略モード（最大化または最小化のいずれか）。デフォルトは最大化です。
