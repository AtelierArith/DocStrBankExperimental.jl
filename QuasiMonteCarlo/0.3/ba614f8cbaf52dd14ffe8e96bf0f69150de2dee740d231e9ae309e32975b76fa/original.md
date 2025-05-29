```julia
MatousekScramble <: ScrambleMethod
```

Linear Matrix Scramble aka Matousek's scramble.

`randomize(x, R::MatousekScramble)` returns a scrambled version of `x`. The scramble method is Linear Matrix Scramble which was introduced in Matousek (1998). `pad` is the number of bits used for each point. One needs `pad ≥ log(base, n)`.

References: Matoušek, J. (1998). On thel2-discrepancy for anchored boxes. Journal of Complexity, 14(4), 527-556.
