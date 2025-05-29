```
H
H(d)
```

Aitchisonによって定義された[`HMatrix`](@ref)のユーザーインターフェース。

`H`は`d` by `d`の行列で、次のように定義できます。

`H[i, j] = I[i, j] + J[i, j]`

## 例

```
julia> H(3)
julia> H*v
julia> v'*H
```
