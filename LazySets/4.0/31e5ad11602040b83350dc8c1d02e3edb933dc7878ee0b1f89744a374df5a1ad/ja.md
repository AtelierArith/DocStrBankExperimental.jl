```
Intersection{N, S1<:LazySet{N}, S2<:LazySet{N}} <: LazySet{N}
```

2つの集合の交差を表す型です。

### フィールド

  * `X`     – 集合
  * `Y`     – 集合
  * `cache` – 再計算を避けるための内部キャッシュ; [`IntersectionCache`](@ref)を参照

### 注意事項

遅延交差の引数が半空間である場合、集合は制約表現のポリヘドロン（`HPolyhedron`）に簡略化されます。

交差は凸性を保持します：集合の引数が凸であれば、その交差も凸です。

### 例

2つの正方形 $X$ と $Y$ の交差を遅延的に表す式 $Z$ を作成します：

```jldoctest lazy_intersection
julia> X, Y = BallInf([0.0, 0.0], 0.5), BallInf([1.0, 0.0], 0.75);

julia> Z = X ∩ Y;

julia> typeof(Z)
Intersection{Float64, BallInf{Float64, Vector{Float64}}, BallInf{Float64, Vector{Float64}}}

julia> dim(Z)
2
```

`isempty`を使って交差が空であるかどうかを確認できます：

```jldoctest lazy_intersection
julia> isempty(Z)
false
```

`Intersection`を小文字の`intersection`関数で計算される具体的な操作と混同しないでください：

```jldoctest lazy_intersection
julia> W = intersection(X, Y)
Hyperrectangle{Float64, Vector{Float64}, Vector{Float64}}([0.375, 0.0], [0.125, 0.5])
```
