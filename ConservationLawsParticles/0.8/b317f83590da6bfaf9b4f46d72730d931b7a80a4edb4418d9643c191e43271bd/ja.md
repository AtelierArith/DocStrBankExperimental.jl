時間を最初の引数として受け取り、それを破棄するメソッドを自動的に定義します。

# 例

定義

```julia
@time_independent V(x) = -x^3
```

は次のように等価です。

```julia
V(x) = -x^3
V(t, x) = V(x)
```

これは、引数が複数の場合でも機能します。例えば、

```julia
@time_independent V(x₁, x₂) = x₁ * x₂
```

は次のように等価です。

```julia
V(x₁, x₂) = x₁ * x₂
V(t, x₁, x₂) = V(x₁, x₂)
```
