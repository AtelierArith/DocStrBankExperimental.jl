```
pawnshift_s(ss::SquareSet)
```

Shift a square set of pawns one step in the 'south' direction.

This is identical to the `shift_s` function except that `pawnshift_s` is a little faster, but will not work for square sets containing squares on the 1st or 8th rank.
