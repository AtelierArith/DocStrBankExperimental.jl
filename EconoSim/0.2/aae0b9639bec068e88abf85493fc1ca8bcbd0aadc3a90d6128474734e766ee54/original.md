```
Restorable
```

Indicates a lifecycle with restorability, i.e. the entity can recover from damage. Thresholds determine the multiplier for health at and below the threshold.

# Fields

  * `damage_thresholds`: These are tuples, ordered by percentage, holding damage multipliers. The applied multiplier corresponds with the lowest threshold which is higher than the health of the entity.
  * `restoration_thresholds`: These are tuples, ordered by percentage, holding restoration multipliers. The applied multiplier corresponds with the lowest threshold which is higher than the health of the entity.
  * `wear`: damage which occurs from each use. Succeptable to multipliers.

# Example

`Restorable     damage_thresholds = [(70.0%, 0.5), (100.0%, 0.2)]     restoration_thresholds = [(40.0%, 0.0), (70.0%, 0.2), (100.0%, 0.3)]` When 1 damage is done it results in 0.2 damage actually being applied. Should health drop to 70% or less, then 0.5 damage would be applied. This indicates the robustness at various levels of damage.

When 1 damage is restored it results in 0.3 damage actually being restored. Should health drop to 40% or below no damage is being restored. This indicates restorability. The last tier indicates a level of damage beyond which no restoration is possible anymore.
