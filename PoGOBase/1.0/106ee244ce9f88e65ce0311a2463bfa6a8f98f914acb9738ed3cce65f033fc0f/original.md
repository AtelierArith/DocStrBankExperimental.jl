```
kmcost(poke::Pokemon, target_level_or_cplimit, candy=0, candyxl=0; add_move=true, as=Species(poke))
```

Estimate the buddy walk distance needed to get enough candy to power up `poke` to `target_level`. `candy` and `candyxl` are the amounts of candy you own and can devote to powering up. `target_level_or_cplimit` is interpreted as a battle league CP limit if it is 500 or larger, otherwise it it interpreted as a target level. Set `add_move=false` if you don't need to purchase a third move.

Note that for XL candy the distance is probabilistic, and the XL rate for walking increases with buddy level, maxing out at level 31: see https://thesilphroad.com/science/quick-discovery/early-look-buddy-candy-xl-rates. If you need to walk to earn XL candy, the calculation assumes that you power up at least to level 31 as quickly as you can (e.g., powering up as you earn regular candy, and waiting to evolve and/or purchase a 3rd move until you reach level 31). Failing to follow this strategy may increase your distance requirement. Alternatively, your distance requirement may decrease if you walk a different pokemon of the same species that is already level 31 or higher.
