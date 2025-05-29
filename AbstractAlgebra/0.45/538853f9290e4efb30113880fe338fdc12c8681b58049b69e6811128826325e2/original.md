```
ppio(a::T, b::T)
```

Return a pair $(c,d)$ such that $a=c*d$ and $c = gcd(a, b^\infty)$ if $a\neq 0$, and $c=b$, $d=0$ if $a=0$.
