```
drop(r)
drop(r; kind=:lowest, n=1)
```

Drops the lowest part of a roll. Notice that for a `DiceRoll`, this means dropping the lowest dice in a roll, but for composite dice, it can mean dropping a whole segment. For instance

```
drop(4d6)
```

will drop the lowest valued dice of the four 6-sided dice rolled. It is equivalent to

```
v = roll.([d6, d6, d6, d6])
sum(v) - minimum(v)
```

On the other hand,

```
drop((2d4 - 1) * (2d4 - 1))
```

will drop the lowest of the product, i.e., it is equivalent to

```
v = roll.([2d4 - 1, 2d4 - 1])
sum(v) - minimum(v)
```

**keyword arguments**

  * `kind`: Either `:lowest` or `:highest` to remove either the lowest or highest roll or rolls.
  * `n`: The number of dice to be removed.
