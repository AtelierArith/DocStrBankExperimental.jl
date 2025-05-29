```
field_amplitude(f, a, b)
```

フィールド振幅の時間積分を次のように計算します。

$$
\int_a^b\diff{t}F(t) = -[A(b) - A(a)],
$$

ここで、$A(t)$は[`vector_potential`](@ref)です。
