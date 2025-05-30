一般化されたアフィン操作（`v = A * u + B * b`）を表し、`AbstractVecOrMat` に適用される可能性があります。ユーザーが提供する更新関数 `update_func[!]` は `AbstractVecOrMat` `b` を更新し、演算子評価中（`L([v,], u, p, t)`）または `update_coefficients[!](L, u, p, t)` への呼び出しによって呼び出されます。更新関数は次の構文を持つと仮定されます。

```
update_func(b::AbstractVecOrMat, u, p, t; <accepted kwargs>) -> new_b
```

または

```
update_func!(b::AbstractVecOrMat, u ,p , t; <accepted kwargs>) -> [modifies b]
```

`B` と `b` は、`A * u + B * b` が意味を持つように適切なサイズを持つことが期待されます。具体的には、`size(A, 1) == size(B, 1)` および `size(u, 2) == size(b, 2)` です。

`update_func[!]` によって受け入れられるキーワード引数のセットは、`AffineOperator` に `accepted_kwargs` というキーワード引数を介して `Symbol` のタプルとして提供されなければなりません。`accepted_kwargs` が提供されていない場合、`kwargs` は `update_func[!]` に渡すことができません。

# 例

```
u = rand(4)
p = rand(4)
t = rand()

A = MatrixOperator(rand(4, 4))
B = MatrixOperator(rand(4, 4))

vec_update_func = (b, u, p, t) -> p * t
L = AffineOperator(A, B, zero(4); update_func = vec_update_func)
L = cache_operator(M, u)

# Lを更新して評価
v = L(u, p, t) # == A * u + B * (p * t)
```
