```
pawnshift_ne(ss::SquareSet)
```

Shift a square set of pawns one step in the 'north east' direction.

This is identical to calling `shift_n` followed by `shift_e`, except that `pawnshift_ne` is a little faster, but will not work for square sets containing squares on the 1st or 8th rank.
