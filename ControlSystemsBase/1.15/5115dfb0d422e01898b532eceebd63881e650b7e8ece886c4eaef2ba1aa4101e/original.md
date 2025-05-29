```
laglink(a, M; [Ts])
```

Returns a phase retarding link, the rule of thumb `a = 0.1ωc` guarantees less than 6 degrees phase margin loss. The bode curve will go from `M`, bend down at `a/M` and level out at 1 for frequencies > `a`

$$
\dfrac{s + a}{s + a/M} = M \dfrac{1 + s/a}{1 + sM/a}
$$
