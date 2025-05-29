```
struct DiamondRelationalConnective{R<:AbstractRelation} <: AbstractRelationalConnective{R} end
struct BoxRelationalConnective{R<:AbstractRelation} <: AbstractRelationalConnective{R} end
```

関係接続詞のシングルトン型で、通常はそれぞれモーダル存在量化子と普遍量化子として解釈されます。

両方の接続詞は、`DiamondRelationalConnective(rel)`のように関係インスタンスで簡単にインスタンス化できます。これは`DiamondRelationalConnective{typeof(rel)}()`のショートカットです。

# 例

```julia-repl
julia> syntaxstring(DiamondRelationalConnective(IA_A))
"⟨A⟩"

julia> syntaxstring(BoxRelationalConnective(IA_A))
"[A]"

julia> @assert DiamondRelationalConnective(IA_A) == SoleLogics.dual(BoxRelationalConnective(IA_A))

```

関連項目としては、[`DiamondRelationalConnective`](@ref)、[`BoxRelationalConnective`](@ref)、[`syntaxstring`](@ref)、[`dual`](@ref)、[`AbstractKripkeStructure`](@ref)、[`AbstractFrame`](@ref)があります。
