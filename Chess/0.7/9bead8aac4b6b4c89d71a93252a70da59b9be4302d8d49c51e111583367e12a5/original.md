```
pawnshift_nw(ss::SquareSet)
```

Shift a square set of pawns one step in the 'north west' direction.

This is identical to calling `shift_n` followed by `shift_w`, except that `pawnshift_nw` is a little faster, but will not work for square sets containing squares on the 1st or 8th rank.
