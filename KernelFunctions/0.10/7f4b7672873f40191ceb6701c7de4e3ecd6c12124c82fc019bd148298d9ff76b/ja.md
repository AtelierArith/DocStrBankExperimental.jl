```
LinearTransform(A::AbstractMatrix)
```

入力の線形変換は行列 `A` によって実現されます。

`A` の第二次元はターゲットの特徴の数と一致する必要があります。

# 例

```jldoctest
julia> A = rand(10, 5); t = LinearTransform(A); X = rand(5, 100);

julia> map(t, ColVecs(X)) == ColVecs(A * X)
true
```
