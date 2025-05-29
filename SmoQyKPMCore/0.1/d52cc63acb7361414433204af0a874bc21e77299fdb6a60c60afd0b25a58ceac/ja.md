```
kpm_eval(x::AbstractFloat, coefs, bounds)
```

$$
F(x)
$$

を評価します。ここで、$x$は区間`bounds[1] < x < bound[2]`内の実数であり、関数$F(\bullet)$はベクトル`coefs`で与えられた係数を持つチェビシェフ展開によって表されます。
