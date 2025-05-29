```
FunctionTransform(f)
```

入力に関数 `f` を適用する変換です。

`f` が入力に作用できることを確認してください。たとえば、入力がベクトルである場合、`f(x) = sin.(x)` のようにする必要があります。`f = sin` の代わりに。

# 例

```jldoctest
julia> f(x) = sum(x); t = FunctionTransform(f); X = randn(100, 10);

julia> map(t, ColVecs(X)) == ColVecs(sum(X; dims=1))
true
```
