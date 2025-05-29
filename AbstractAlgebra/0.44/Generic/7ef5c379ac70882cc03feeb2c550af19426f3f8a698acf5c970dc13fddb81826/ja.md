```
cycles(g::Perm)
```

置換 `g` を互いに素なサイクルに分解します。

互いに素なサイクルの反復を行う `CycleDec` オブジェクトを返します。サイクルの順序は保証されず、各サイクル内の順序は循環置換まで計算されます。サイクル分解は `g` にキャッシュされ、将来の `permtype`、`parity`、`sign`、`order` および `^`（累乗）の計算に使用されます。

# 例

```jldoctest
julia> g = Perm([3,4,5,2,1,6])
(1,3,5)(2,4)

julia> collect(cycles(g))
3-element Vector{Vector{Int64}}:
 [1, 3, 5]
 [2, 4]
 [6]
```
