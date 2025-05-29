```
leadlink(b, N, K=1; [Ts])
```

Returns a phase advancing link, the top of the phase curve is located at `ω = b√(N)` where the link amplification is `K√(N)` The bode curve will go from `K`, bend up at `b` and level out at `KN` for frequencies > `bN`

The phase advance at `ω = b√(N)` can be plotted as a function of `N` with `leadlinkcurve()`

Values of `N < 1` will give a phase retarding link.

$$
KN \dfrac{s + b}{s + bN} = K \dfrac{1 + s/b}{1 + s/(bN)}
$$

See also `leadlinkat` `laglink`
