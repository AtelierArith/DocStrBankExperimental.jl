```
abstract type AbstractRelation end
```

多モーダル注釈付きアクセシビリティグラフ（クリプキ構造）の関係のための抽象型です。注目すべき2つの関係は、現在の世界とすべての世界にアクセスする`identityrel`と`globalrel`です。

# 例

```julia-repl
julia> fr = SoleLogics.FullDimensionalFrame((10,),);

julia> Interval(8,11) in (accessibles(fr, Interval(2,5), IA_L))
true
```

# 実装

新しい関係型`R`を実装する際は、次のメソッドを提供してください：

```
arity(::R)::Int = ...
syntaxstring(::R; kwargs...)::String = ...
```

関係が対称である場合は、その逆関係`cr`を次のように指定してください：

```
hasconverse(::R) = true
converse(::R) = cr
```

関係が多対一または一対一である場合は、次のようにフラグを立ててください：

```
istoone(::R) = true
```

関係が反射的または推移的である場合は、次のようにフラグを立ててください：

```
isreflexive(::R) = true
istransitive(::R) = true
```

最も重要なことは、`R`の論理的意味論は`accessibles`メソッドを通じて定義されるべきであり、`accessibles`のヘルプを参照してください。

また、[`issymmetric`](@ref)、[`isreflexive`](@ref)、[`istransitive`](@ref)、[`isgrounding`](@ref)、[`arity`](@ref)、[`syntaxstring`](@ref)、[`converse`](@ref)、[`hasconverse`](@ref)、[`istoone`](@ref)、[`identityrel`](@ref)、[`globalrel`](@ref)、[`accessibles`](@ref)、[`AbstractKripkeStructure`](@ref)、[`AbstractFrame`](@ref)、[`AbstractWorld`](@ref)も参照してください。
