```julia
sitegroup(
    sg::Crystalline.SpaceGroup{D},
    wp::Crystalline.WyckoffPosition{D}
) -> Crystalline.SiteGroup

```

空間群 `sg` のワイコフ位置 `wp` に対するサイト対称群 `g::SiteGroup` を返します（または空間群番号 `sgnum` を使用する場合；この場合、次元性は `wp` から推測されます）。

`g` は、格子ベクトルによって異なる可能性があるという意味で `sg` にリストされている操作と同型であり、ワイコフ位置 `wp` を不変に保つ操作の群であり、`all(op -> wp == compose(op, wp), g) == true` となります。

返される `SiteGroup` には、ワイコフ位置のコセット代表も含まれており（これも再び `sg` に登場するものと同型です）、[`cosets`](@ref) を介してアクセス可能で、例えばワイコフ位置の軌道を生成します（[`orbit(::SiteGroup)`](@ref) を参照）し、`g` の要素と共に `sg` の左コセット分解を定義します。

## 例

```jldoctest sitegroup
julia> sgnum = 16;

julia> D = 2;

julia> wp = wyckoffs(sgnum, D)[3] # ワイコフ位置を選択
2b: [1/3, 2/3]

julia> sg = spacegroup(sgnum, D);

julia> g  = sitegroup(sg, wp)
SiteGroup{2} ⋕16 (p6) at 2b = [1/3, 2/3] with 3 operations:
 1
 {3⁺|1,1}
 {3⁻|0,1}
```

`SiteGroup` の群構造は `MultTable` で調べることができます：

```jldoctest sitegroup
julia> MultTable(g)
3×3 MultTable{SymOperation{2}}:
──────────┬──────────────────────────────
          │        1  {3⁺|1,1}  {3⁻|0,1} 
──────────┼──────────────────────────────
        1 │        1  {3⁺|1,1}  {3⁻|0,1} 
 {3⁺|1,1} │ {3⁺|1,1}  {3⁻|0,1}         1
 {3⁻|0,1} │ {3⁻|0,1}         1  {3⁺|1,1}
──────────┴──────────────────────────────
```

元の空間群は、`SiteGroup` に含まれる操作とコセットを使用して左コセット分解から再構築できます：

```jldoctest sitegroup
julia> ops = [opʰ*opᵍ for opʰ in cosets(g) for opᵍ in g];

julia> Set(sg) == Set(ops)
true
```

## 用語

数学的には、サイト対称群はワイコフ位置のための *安定化群* であり、**k**-点のための小群が安定化群であるのと同じ意味です。

与えられた空間群のすべてのサイト対称群の計算については、[`sitegroups`](@ref) も参照してください。
