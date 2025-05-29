```
setdash(dashes::Vector, offset=0.0)
```

Set the dash pattern for lines to the values in `dashes`. The first number is the length of the inked portion, the second the space, and so on.

The `offset` specifies an offset into the pattern at which the stroke begins. So an offset of 10 means that the stroke starts at `dashes[1] + 10` into the pattern.

Or use `setdash("dot")` etc.
