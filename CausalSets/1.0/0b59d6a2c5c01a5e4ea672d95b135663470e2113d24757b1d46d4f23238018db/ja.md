```
ConformallyTimesliceableManifold{N} <: AbstractManifold{M}
```

$$
N
$$

次元の準同型タイムスライス可能多様体のスーパークラスであり、メトリックが次の形に持ち込まれる多様体として定義されます。

$$
\begin{aligned}
\mathrm{d}s^2 = F \left( -\mathrm{d}t^2 + \mathrm{d}X^2 \right)
\end{aligned}
$$

ここで、$F$は準同型因子であり、$\mathrm{d} X^2$は何らかの$N-1$次元の空間的線要素です。
