```
struct JointLife
    lives
    contingency
    joint_assumption
end

A `Life`オブジェクトは、共同生命保険に関連する条件付き数学のために必要な仮定を含んでいます。多くのアクチュアリー現在価値計算を行うために`LifeContingency`と共に使用します。

キーワード引数:

  * `lives`は2つの`SingleLife`のタプルです
  * `contingency`のデフォルトは`LastSurvivor()`です。これは条件付き給付のトリガーです。`?Contingency`を参照してください。
  * `joint_assumption`のデフォルト値は`Frasier()`です。これは2つの生命の死亡率の間の仮定された関係です。`?JointAssumption`を参照してください。

# 例

```

using MortalityTables mortality = MortalityTables.table("2001 VBT Residual Standard Select and Ultimate - Male Nonsmoker, ANB")

l1 = SingleLife(     mortality       = mortality.select[30],      issue*age  = 30           ) l2 = SingleLife(     mortality       = mortality.select[30],      issue*age  = 30           )

jl = JointLife(     lives = (l1,l2),     contingency = LastSurvivor(),     joint_assumption = Frasier() ) ```
