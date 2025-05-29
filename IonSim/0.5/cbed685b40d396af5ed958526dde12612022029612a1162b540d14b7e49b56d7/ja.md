```
sigma(ion::Ion, ψ1::sublevel[, ψ2::sublevel])
```

$$
|ψ1\rangle\langle ψ2|
$$

を返します。ここで、$|ψ_i\rangle$は`ion[ψᵢ]`によって返される状態に対応します。

ψ2が指定されていない場合、$|ψ1\rangle\langle ψ1|$が返されます。
