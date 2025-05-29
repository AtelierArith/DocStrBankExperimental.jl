```
flux(u, orientation_or_normal, equations)
```

与えられた保存変数 `u` に対して、対応する支配方程式のために、直交方向 `orientation::Integer` または任意の方向 `normal::AbstractVector` における（物理的な）フラックスを計算します。`orientation` は x-, y-, z-方向に対してそれぞれ `1`、`2`、`3` です。
