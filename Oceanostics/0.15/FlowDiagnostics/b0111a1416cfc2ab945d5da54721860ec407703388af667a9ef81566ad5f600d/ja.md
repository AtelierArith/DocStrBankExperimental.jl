```julia
DirectionalErtelPotentialVorticity(
    model,
    direction;
    tracer,
    location
)

```

与えられた `direction` からのErtelポテンシャル渦度への寄与を、`model` と `direction` に基づいて計算します。Ertelポテンシャル渦度は次のように定義されます。

```
EPV = ωₜₒₜ ⋅ ∇b
```

ここで、ωₜₒₜ は全体（相対 + 惑星的）渦度ベクトル、`b` は浮力、∇ は勾配演算子です。
