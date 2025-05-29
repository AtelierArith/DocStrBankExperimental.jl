```
pawnshift_se(ss::SquareSet)
```

Shift a square set of pawns one step in the 'south east' direction.

This is identical to calling `shift_s` followed by `shift_e`, except that `pawnshift_se` is a little faster, but will not work for square sets containing squares on the 1st or 8th rank.
