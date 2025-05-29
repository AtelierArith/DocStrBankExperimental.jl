```
XPRS_PREPROBING
```

Presolve: Amount of probing to perform on binary variables during presolve. (integer)

This is done by fixing a binary to each of its values in turn and analyzing the implications.

Default value: `-1`

Values: -1 : Let the optimizer decide on the amount of probing. 0 : Disabled. +1 : Light probing only few implications will be examined. +2 : Full probing all implications for all binaries will be examined. +3 : Full probing and repeat as long as the problem is significantly reduced.
