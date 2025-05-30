# sim_happiness

```julia
sim_happiness(; seed, n_years, max_age, n_births, aom)

```

幸福をシミュレートします。ルールは書籍のセクション6.3に基づいています：

  * 毎年、20人が均等に分布した幸福値で生まれます。
  * 毎年、各人は1歳年を取ります。幸福は変わりません。
  * 18歳で、個人は結婚することができます。毎年の結婚の確率は

個人の幸福に比例します。

  * 一度結婚すると、個人は結婚したままです。
  * 65歳を過ぎると、個人はサンプルから離れます。（彼らはスペインに移動します。）

引数：

  * `seed`: ランダムシード、デフォルトはシードなし
  * `n_years`: シミュレートする年数
  * `max_age`: 人々が生きる最大年齢
  * `n_births`: 毎年生まれる人の数
  * `aom`: 人々が結婚できる年齢

# 例

```jldoctest
julia> using StatisticalRethinking

julia> sim_happiness(n_years=4, n_births=10)
40×3 DataFrame
 Row │ age    happiness  married
     │ Int64  Float64    Int64
─────┼───────────────────────────
   1 │     4  -2.0             0
   2 │     4  -1.55556         0
   3 │     4  -1.11111         0
```
