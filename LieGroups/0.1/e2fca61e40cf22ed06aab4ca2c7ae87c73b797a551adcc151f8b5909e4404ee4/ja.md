```
apply(A::GroupAction{T, L, M}, g, p)
apply!(A::GroupAction{T, L, M}, q, g, p)
```

$$
g ∈ \mathcal G
$$

によって誘導される群作用を $p ∈ \mathcal M$ に適用します。群作用の種類は [`AbstractGroupActionType`](@ref) `T` によって示されます。これは `q` のインプレースで実行できます。
