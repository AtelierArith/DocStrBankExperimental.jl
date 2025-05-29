```julia
struct CatRules{NextItemRuleT<:ComputerAdaptiveTesting.NextItemRules.NextItemRule, TerminationConditionT<:ComputerAdaptiveTesting.TerminationConditions.TerminationCondition, AbilityEstimatorT<:ComputerAdaptiveTesting.Aggregators.AbilityEstimator, AbilityTrackerT<:ComputerAdaptiveTesting.Aggregators.AbilityTracker} <: ComputerAdaptiveTesting.ConfigBase.CatConfigBase
```

  * `next_item::ComputerAdaptiveTesting.NextItemRules.NextItemRule`: 現在の状態に基づいてCATで次のアイテムを選択するためのルール。
  * `termination_condition::ComputerAdaptiveTesting.TerminationConditions.TerminationCondition`: CATを終了するタイミングを選択するためのルール。
  * `ability_estimator::ComputerAdaptiveTesting.Aggregators.AbilityEstimator`: テストを受ける者の現在の能力を推定する能力推定器。
  * `ability_tracker::ComputerAdaptiveTesting.Aggregators.AbilityTracker`: テストを受ける者の現在の能力レベルを追跡する能力トラッカー。 デフォルト: NullAbilityTracker()

CATのルールの設定。これにはCATの操作に必要な基本的なルールがすべて含まれていますが、アイテムバンクやCATを実行するために必要なインタラクティビティフックは含まれていません。

フックを使用するのではなく、自分自身のCATループを書く場合、CatLoopConfigよりも統合しやすいレイヤーかもしれません。

```
CatRules(; next_item=..., termination_condition=..., ability_estimator=..., ability_tracker=...)
```

CatRulesの明示的なコンストラクタ。

```
CatRules(bits...)
```

CatRulesの暗黙的なコンストラクタ。
