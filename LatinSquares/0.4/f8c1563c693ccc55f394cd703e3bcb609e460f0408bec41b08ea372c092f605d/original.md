`latin(n)` returns a simple `n`-by-`n` Latin square. More generally, `latin(n,a,b)` generates a Latin square whose `i,j`-entry is `a*(i-1) + b*(j-1) + 1` (wrapping around `n`, of course).

*Note*: If parameters `n,a,b` do not generate a legitimate Latin square an error is thrown.
