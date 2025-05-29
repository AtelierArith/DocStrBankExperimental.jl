```
damage(move::AbstractMove, attacker, defender; kwargs...)
```

Calculate the damage caused by a `move` from `attacker` against `defender`. If `defender` is a `Pokemon`, the damage is an integer number of HP. If `defender` is a `BossFT`, the damage is a percentage of the boss's HP.

Allowed `kwargs` depend on whether `move` is a PvP or PvE move.

For PvP moves, the following `kwargs` are allowed:

  * `buffs::Real`: a multiplier for the damage, default is 1
  * `charge::Real`: a multiplier for the damage, default is 1

For PvE moves, the following `kwargs` are allowed:

  * `current_weather`: the current weather, default is missing (alternatively supply a numeric `weather=1.2` directly)
  * `friendship`: the friendship level, default is missing (alternatively supply a numeric `friendshipbonus=1.0` directly)
  * `dodged`: a multiplier for the damage, default is 1
  * `mushroom::Bool`: a flag for the mushroom effect, default is false
  * `helpericons`: the number of helper icons, default is 0 (alternatively supply a numeric `helperbonus=1.0` directly)
  * `attack_multiplier`: a multiplier for the attacker's attack, default is 1
  * `defense_multiplier`: a multiplier for the defender's defense, default is 1
