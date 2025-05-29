```
statproducts_league(pd, league_cp; level_limit=50.0, iv_floor=0) → statprods
```

Calculates the stat product associated with each possible IV combination. `statprods[a, d, h]` returns the stat-product for `pd` with IVs `(a, d, h)`. Note indexing of `statprods` starts at 0.

`level_limit` sets the power-up limit, and `iv_floor` sets the minimum IV in all three categories. The following floors apply:

  * raids, egg hatches, and research: 10
  * weather boosted: 4
  * trades:

      * good friends: 1
      * great friends: 2
      * ultra friends: 3
      * best friends: 5
      * lucky: 12

`statprods[a, d, h]` is zero for any IV combination not meeting these requirements.
