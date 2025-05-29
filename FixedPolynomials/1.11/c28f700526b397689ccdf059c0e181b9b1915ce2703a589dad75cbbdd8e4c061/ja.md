```
GradientConfig(f::Polynomial{T}, [x::AbstractVector{S}])
```

`f`の勾配を効率的に評価できるデータ構造です。`x`は`f(x)`の出力型を決定するためだけに使用されることに注意してください。

```
GradientConfig(f::Polynomial{T}, [S])
```

ベクトル`x`の代わりに、型を直接指定することもできます。
