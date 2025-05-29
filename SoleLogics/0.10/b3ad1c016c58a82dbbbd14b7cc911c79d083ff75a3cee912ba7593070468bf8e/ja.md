```
accessibles(
    fr::AbstractMultiModalFrame{W},
    w::W,
    r::AbstractRelation
) where {W<:AbstractWorld}
```

フレーム `fr` から世界 `w` を介して関係 `r` によってアクセス可能な世界を返します。

# 例

```julia-repl
julia> fr = SoleLogics.FullDimensionalFrame((10,),);

julia> typeof(accessibles(fr, Interval(2,5), IA_L))
Base.Generator{...}

julia> typeof(accessibles(fr, globalrel))
Base.Generator{...}

julia> @assert SoleLogics.nworlds(fr) == length(collect(accessibles(fr, globalrel)))

julia> typeof(accessibles(fr, Interval(2,5), identityrel))
Vector{Interval{Int64}}

julia> Interval(8,11) in collect(accessibles(fr, Interval(2,5), IA_L))
true
```

# 実装

`accessibles` は常に同じ型 `W` の世界のイテレータを返すため、マルチモーダルフレームの `accessibles` の現在の実装は、列挙を低レベルの `_accessibles` 関数に委任します。この関数は、パラメータタプルのイテレータを返し、それが IterTools ジェネレータを使用して世界コンストラクタに供給されます。以下のように：

```
function accessibles(
    fr::AbstractMultiModalFrame{W},
    w::W,
    r::AbstractRelation,
) where {W<:AbstractWorld}
    IterTools.imap(W, _accessibles(fr, w, r))
end
```

そのため、新しいフレーム、世界、および/または関係を定義する際には、`_accessibles` の新しいメソッドを提供する必要があります。例えば：

```
_accessibles(fr::Full1DFrame, w::Interval{<:Integer}, ::_IA_A) = zip(Iterators.repeated(w.y), w.y+1:X(fr)+1)
```

このパターンは一般的に便利ですが、回避することも可能ですが、これにはディスパッチの曖昧さを解決するために2つの追加メソッドを定義する必要があります。新しいフレームタイプ `FR{W}` を定義する際には、これらの3つのメソッドを提供することで曖昧さを解決し、カスタム `accessibles` メソッドを定義できます：

```
# 関係 `r` を介して世界にアクセス
function accessibles(
    fr::FR{W},
    w::W,
    r::AbstractRelation,
) where {W<:AbstractWorld}
    ...
end

# 現在の世界にアクセス
function accessibles(
    fr::FR{W},
    w::W,
    r::IdentityRel,
) where {W<:AbstractWorld}
    [w]
end

# すべての世界にアクセス
function accessibles(
    fr::FR{W},
    w::W,
    r::GlobalRel,
) where {W<:AbstractWorld}
    allworlds(fr)
end
```

一般的に、`collect(accessibles(fr, w, r)) isa AbstractWorlds{W}` であるべきです。

詳細は [`AbstractWorld`](@ref)、[`AbstractRelation`](@ref)、[`AbstractMultiModalFrame`](@ref) を参照してください。
