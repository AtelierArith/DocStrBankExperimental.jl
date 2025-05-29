```
gradient_magnitude(l::PyObject, o::Union{Array, PyObject})
```

勾配の合計を返します 

$$
\sqrt{\sum_{i=1}^n \|\frac{\partial l}{\partial o_i}\|^2}
$$

この関数はトレーニングのデバッグに役立ちます。
