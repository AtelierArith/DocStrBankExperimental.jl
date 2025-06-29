# sim_happiness

```julia
sim_happiness(; seed, n_years, max_age, n_births, aom)

```

Simulates hapiness using rules from section 6.3 of the book:

  * Each year, 20 people are born with uniformly distributed happiness values.
  * Each year, each person ages one year. Happiness does not change.
  * At age 18, individuals can become married. The odds of marriage each year are

proportional to an individual’s happiness.

  * Once married, an individual remains married.
  * After age 65, individuals leave the sample. (They move to Spain.)

Arguments:

  * `seed`: random seed, default is no seed
  * `n_years`: amount of years to simulate
  * `max_age`: maximum age people are living
  * `n_births`: count of people are born every year
  * `aom`: at what age people can got married

# Examples

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
