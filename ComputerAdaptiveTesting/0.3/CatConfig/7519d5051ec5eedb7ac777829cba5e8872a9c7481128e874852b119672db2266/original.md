```julia
struct CatRules{NextItemRuleT<:ComputerAdaptiveTesting.NextItemRules.NextItemRule, TerminationConditionT<:ComputerAdaptiveTesting.TerminationConditions.TerminationCondition, AbilityEstimatorT<:ComputerAdaptiveTesting.Aggregators.AbilityEstimator, AbilityTrackerT<:ComputerAdaptiveTesting.Aggregators.AbilityTracker} <: ComputerAdaptiveTesting.ConfigBase.CatConfigBase
```

  * `next_item::ComputerAdaptiveTesting.NextItemRules.NextItemRule`: The rule to choose the next item in the CAT given the current state.

  * `termination_condition::ComputerAdaptiveTesting.TerminationConditions.TerminationCondition`: The rule to choose when to terminate the CAT.

  * `ability_estimator::ComputerAdaptiveTesting.Aggregators.AbilityEstimator`: The ability estimator, which estimates the testee's current ability.

  * `ability_tracker::ComputerAdaptiveTesting.Aggregators.AbilityTracker`: The ability tracker, which tracks the testee's current ability level.  Default: NullAbilityTracker()

Configuration of the rules for a CAT. This all includes all the basic rules for the CAT's operation, but not the item bank, nor any of the interactivity hooks needed to actually run the CAT.

This may be more a more convenient layer to integrate than CatLoopConfig if you want to write your own CAT loop rather than using hooks.

```
CatRules(; next_item=..., termination_condition=..., ability_estimator=..., ability_tracker=...)
```

Explicit constructor for CatRules.

```
CatRules(bits...)
```

Implicit constructor for CatRules.
