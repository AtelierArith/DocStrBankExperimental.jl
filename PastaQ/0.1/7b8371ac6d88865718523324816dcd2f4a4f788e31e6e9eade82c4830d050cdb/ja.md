```
productstate(hilbert::Vector{<:Index})
productstate(n::Int; dim = 2)
```

生成されたMPS波動関数は、次の積状態に対応します。

$$
|\psi\rangle = |0\rangle_1\otimes|0\rangle_2\otimes\dots|0\rangle_n
$$

これは、ヒルベルト空間またはモードの数と局所次元の両方を受け入れます。
