```julia
canonicalize!(
    state::QuantumClifford.AbstractStabilizer;
    phases,
    ranks
) -> Union{Tuple{QuantumClifford.AbstractStabilizer, Int64, Int64}, QuantumClifford.AbstractStabilizer}

```

安定器を正準化します（インプレース）。

入力が有効な安定器であることを前提としています（すべての演算子が可換で、実数の位相を持つ）。冗長な生成子や単位生成子を許可します。

```jldoctest
julia> ghz = S"XXXX
               ZZII
               IZZI
               IIZZ";


julia> canonicalize!(ghz)
+ XXXX
+ Z__Z
+ _Z_Z
+ __ZZ

julia> canonicalize!(S"XXXX
                       IZZI
                       IIZZ")
+ XXXX
+ _Z_Z
+ __ZZ
```

次の例の表のすべての行が独立しているわけではありません：

```jldoctest
julia> canonicalize!(S"XXXX
                       ZZII
                       IZZI
                       IZIZ
                       IIZZ")
+ XXXX
+ Z__Z
+ _Z_Z
+ __ZZ
+ ____
```

ランクが低い場合、より高度な表構造が適しているかもしれません。たとえば、[`MixedStabilizer`](@ref) や [`MixedDestabilizer`](@ref) 構造（これらについては、ドキュメントの [データ構造のセクション](@ref Choosing-Appropriate-Data-Structure) で詳しく読むことができます）。

`phases=false` が設定されている場合、正準化は表の位相を追跡せず、重要な（定数因子の）速度向上をもたらします。

```jldoctest
julia> s = S"-ZX
              XZ"
- ZX
+ XZ

julia> canonicalize!(copy(s), phases=false)
- XZ
+ ZX

julia> canonicalize!(copy(s))
+ XZ
- ZX
```

`ranks=true` が設定されている場合、正準化の X および Z ステージの最後のピボットインデックスも返されます。

```jldoctest
julia> s = S"XXXX
             ZZII
             IZIZ
             ZIIZ";


julia> _, ix, iz = canonicalize!(s, ranks=true); ix, iz
(1, 3)

julia> s
+ XXXX
+ Z__Z
+ _Z_Z
+ ____
```

[garcia2012efficient](@cite) に基づいています。

関連項目：[`canonicalize_rref!`](@ref)、[`canonicalize_gott!`](@ref)
