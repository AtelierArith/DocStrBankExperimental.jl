```
keep(r)
keep(r; kind=:highest, n=1)
```

Keep only the highest part of a roll. Notice that for a `DiceRoll`, this means keeping the largest dice in a roll, but for composite dice, it can mean keeping a whole segment. See the behaviour of `drop` for more information.

**keyword arguments**

  * `kind`: Either `:lowest` or `:highest` to keep either the lowest or highest roll or rolls.
  * `n`: The number of dice to be kept.
