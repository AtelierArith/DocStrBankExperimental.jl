```
Base.sum(x::Convex.AbstractExpr; dims = :)
```

`x`を合計し、オプションで次元`dims`に沿って合計します。

## 例

式内のすべての要素を合計します：

```jldoctest; filter=r"id: [0-9]+…[0-9]+"
julia> x = Variable(2, 2);

julia> atom = sum(x)
sum (affine; real)
└─ 2×2 real variable (id: 263…449)

julia> size(atom)
(1, 1)
```

最初の次元に沿って合計し、行ベクトルを作成します：

```jldoctest; filter=r"id: [0-9]+…[0-9]+"
julia> x = Variable(2, 2);

julia> atom = sum(x; dims = 1)
* (affine; real)
├─ [1.0 1.0]
└─ 2×2 real variable (id: 143…826)

julia> size(atom)
(1, 2)
```

2番目の次元に沿って合計し、列ベクトルを作成します：

```jldoctest; filter=r"id: [0-9]+…[0-9]+"
julia> atom = sum(x; dims = 2)
* (affine; real)
├─ 2×2 real variable (id: 143…826)
└─ [1.0; 1.0;;]

julia> size(atom)
(2, 1)
```
