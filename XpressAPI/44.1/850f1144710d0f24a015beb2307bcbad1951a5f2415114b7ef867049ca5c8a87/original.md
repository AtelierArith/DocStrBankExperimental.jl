```
XPRS_PREPERMUTE
```

This bit vector control specifies whether to randomly permute rows, columns and MIP entities when starting the presolve. (integer)

With the default value `0`, no permutation will take place.

Default value: `0`

Values are a bitset: bit 0 : Permute rows. bit 1 : Permute columns. bit 2 : Permute MIP entities. This bit only affects MIP problems.
