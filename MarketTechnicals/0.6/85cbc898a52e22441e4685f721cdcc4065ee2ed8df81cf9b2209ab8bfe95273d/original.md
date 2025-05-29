```
bollingerbands(ta::TimeArray, ma=20, width=2.0)
```

Bollinger Bands

# Formula

$$
\begin{align*}
  \text{Up}   & = \text{SMA} + \text{width} \times \sigma(P) \\
  \text{Mean} & = \text{SMA} \\
  \text{Down} & = \text{SMA} - \text{width} \times \sigma(P)
\end{align*}
$$
