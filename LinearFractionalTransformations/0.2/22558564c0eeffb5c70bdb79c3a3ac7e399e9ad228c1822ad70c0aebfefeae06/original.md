```
LFT
```

A linear fractional transformation `f(z)=(a*z+b)/(c*z+d)` where `a,b,c,d` are complex numbers.

Constructors:

  * `LFT(a,b,c,d)`: create the function described above.
  * `LFT()`: create the identity function `f(z) = z`. Equivalent to `LFT(1,0,0,1)`.
  * `LFT(a,b,c)`: create the function with `a ↦ 0`, `b ↦ 1`, and `c ↦ ∞`.
  * `LFT(a,aa,b,bb,c,cc)` or `LFT(a=>aa,b=>bb,c=>cc)`: creates the function with `a ↦ aa`, `b ↦ bb`, and `c ↦ cc`.
