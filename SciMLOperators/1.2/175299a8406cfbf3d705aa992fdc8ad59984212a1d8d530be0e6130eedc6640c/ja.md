一般化されたアフィン操作（`w = A * v + B * b`）を表し、`AbstractVecOrMat` に適用される可能性があります。ユーザーが提供する更新関数 `update_func[!]` は `AbstractVecOrMat` `b` を更新し、演算子評価中（`L([w,], v, u, p, t)`）または `update_coefficients[!](L, u, p, t)` への呼び出しによって呼び出されます。更新関数は次の構文を持つと仮定されます。

```
update_func(b::AbstractVecOrMat, u, p, t; <accepted kwargs>) -> new_b
```

または

```
update_func!(b::AbstractVecOrMat, u ,p , t; <accepted kwargs>) -> [modifies b]
```

`B` と `b` は、`A * v + B * b` が意味を持つように適切なサイズを持つことが期待されます。具体的には、`size(A, 1) == size(B, 1)` および `size(v, 2) == size(b, 2)` です。

`update_func[!]` が受け入れるキーワード引数のセットは、`AffineOperator` に `accepted_kwargs` というキーワード引数を介して `Symbol` のタプルとして提供されなければなりません。`accepted_kwargs` が提供されていない場合、`kwargs` を `update_func[!]` に渡すことはできません。

# 例

```
v = rand(4)
u = rand(4)
p = rand(4)
t = rand()

A = MatrixOperator(rand(4, 4))
B = MatrixOperator(rand(4, 4))

vec_update_func = (b, u, p, t) -> p .* u * t
L = AffineOperator(A, B, zero(4); update_func = vec_update_func)
L = cache_operator(M, v)

# Lを更新して評価
w = L(v, u, p, t) # == A * v + B * (p .* u * t)
```
