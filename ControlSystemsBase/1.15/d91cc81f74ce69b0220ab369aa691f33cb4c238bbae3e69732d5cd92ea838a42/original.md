```
leadlinkat(ω, N, K=1; [Ts])
```

Returns a phase advancing link, the top of the phase curve is located at `ω` where the link amplification is `K√(N)` The bode curve will go from `K`, bend up at `ω/√(N)` and level out at `KN` for frequencies > `ω√(N)`

The phase advance at `ω` can be plotted as a function of `N` with `leadlinkcurve()`

Values of `N < 1` will give a phase retarding link.

See also `leadlink` `laglink`
