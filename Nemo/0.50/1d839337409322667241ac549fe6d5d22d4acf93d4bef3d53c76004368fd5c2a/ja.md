```
Float64(x::RealFieldElem, round::RoundingMode=RoundNearest)
```

$$
x
$$

を`Float64`に変換し、$round$で指定された方向に丸めます。`RoundNearest`の場合、返される値は$x$の中点を近似します。`RoundDown`または`RoundUp`の場合、返される値は$x$のすべての値に対する下限または上限です。
