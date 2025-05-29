```julia
OwenScramble <: ScrambleMethod
```

Nested Uniform Scramble aka Owen's scramble.

`randomize(x, R::OwenScramble)` returns a scrambled version of `x`. The scramble method is Nested Uniform Scramble which was introduced in Owen (1995). `pad` is the number of bits used for each point. One needs `pad ≥ log(base, n)`.

References: Owen, A. B. (1995). Randomly permuted (t, m, s)-nets and (t, s)-sequences. In Monte Carlo and Quasi-Monte Carlo Methods in Scientific Computing: Proceedings of a conference at the University of Nevada, Las Vegas, Nevada, USA, June 23–25, 1994 (pp. 299-317). Springer New York.
