```
XPRS_PRIMALOPS
```

Primal simplex: allows fine tuning the variable selection in the primal simplex solver. (integer)

Default value: `-1`

Values are a bitset: bit 0 : Use aggressive dj scaling. bit 1 : Conventional dj scaling. bit 2 : Use reluctant switching back to partial pricing. bit 3 : Use dynamic switching between cheap and expensive pricing strategies. bit 4 : Keep solving even after potential cycling is detected.
