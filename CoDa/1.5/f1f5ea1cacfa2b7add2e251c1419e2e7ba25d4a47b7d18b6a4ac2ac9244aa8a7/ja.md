```
G
G(D)
```

Aitchisonによって定義された[`GMatrix`](@ref)のユーザーインターフェース。

`G`は`D` by `D`の行列で、次のように定義できます。

`G[i, j] = I[i, j] - J[i, j] / D`

## 例

```
julia> G(3)
julia> G*v
julia> v'*G
```
