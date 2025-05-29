```
pawnshift_n(ss::SquareSet)
```

Shift a square set of pawns one step in the 'north' direction.

This is identical to the `shift_n` function except that `pawnshift_n` is a little faster, but will not work for square sets containing squares on the 1st or 8th rank.
