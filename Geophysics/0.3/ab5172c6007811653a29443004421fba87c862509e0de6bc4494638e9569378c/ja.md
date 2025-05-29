```
aspectratio(P::Planet) = semiminor(P)/semimajor(P)
```

`Planet`の`semimajor`に対する`aspectratio`または`semiminor`の値（無次元）。

```Julia
julia> aspectratio(Earth)
0.9966471893352525
```
