```
damage(move::AbstractMove, attacker, defender; kwargs...)
```

`attacker`から`defender`に対する`move`によって引き起こされるダメージを計算します。`defender`が`Pokemon`の場合、ダメージはHPの整数値です。`defender`が`BossFT`の場合、ダメージはボスのHPのパーセンテージです。

許可される`kwargs`は、`move`がPvPかPvEかによって異なります。

PvPの技の場合、次の`kwargs`が許可されます：

  * `buffs::Real`: ダメージの乗数、デフォルトは1
  * `charge::Real`: ダメージの乗数、デフォルトは1

PvEの技の場合、次の`kwargs`が許可されます：

  * `current_weather`: 現在の天候、デフォルトはmissing（代わりに数値`weather=1.2`を直接指定）
  * `friendship`: 友情レベル、デフォルトはmissing（代わりに数値`friendshipbonus=1.0`を直接指定）
  * `dodged`: ダメージの乗数、デフォルトは1
  * `mushroom::Bool`: マッシュルーム効果のフラグ、デフォルトはfalse
  * `helpericons`: ヘルパーアイコンの数、デフォルトは0（代わりに数値`helperbonus=1.0`を直接指定）
  * `attack_multiplier`: 攻撃者の攻撃の乗数、デフォルトは1
  * `defense_multiplier`: 防御者の防御の乗数、デフォルトは1

```
