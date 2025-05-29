```
Y = transform_moments(X::Matrix, m, Σ; preserve_latin=false)
```

`X`を変換して、指定された平均と共分散を得るようにします。

```julia
m, Σ   = [1,2], [2 1; 1 4] # 望ましい平均と共分散
particles = transform_moments(X, m, Σ)
julia> cov(particles) ≈ Σ
true
```

**注意**、もし`X`がラテンハイパーキューブであり、`Σ`が非対角行列である場合、ラテン特性は最初の次元を除くすべての次元で破壊されます。すべての次元でラテン特性を完全に保持するメソッド`preserve_latin=true`を提供しますが、これを使用するとサンプルの共分散がわずかに間違ってしまいます。
