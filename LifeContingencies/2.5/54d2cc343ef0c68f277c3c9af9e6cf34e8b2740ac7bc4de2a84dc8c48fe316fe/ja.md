```
struct SingleLife
    mortality
    issue_age::Int
    alive::Bool
    fractional_assump::MortalityTables.DeathDistribution
end
```

単一の生命に関連する条件付き数学のために必要な仮定を含む `Life` オブジェクト。多くのアクチュアリー現在価値計算を行うために `LifeContingency` と一緒に使用します。

キーワード引数:

  * `mortality` 適用可能な死亡率の配列で、達成年齢によってインデックス付けされた死亡率ベクトルを渡します。
  * `issue_age` は `SingleLife` の仮定された発行年齢であり、多くの条件付き計算の基礎となります。
  * `alive` デフォルト値は `true` です。保険に加入している生命の異なる状態に対して共同保険に便利です。
  * `fractional_assump` デフォルト値は `Uniform()` です。これは `MortalityTables.jl` パッケージの `DeathDistribution` であり、非整数の年齢/時間に使用する仮定です。

# 例

```
using MortalityTables
mortality = MortalityTables.table("2001 VBT Residual Standard Select and Ultimate - Male Nonsmoker, ANB")

SingleLife(
    mort       = mort.select[30], 
    issue_age  = 30          
)
```
