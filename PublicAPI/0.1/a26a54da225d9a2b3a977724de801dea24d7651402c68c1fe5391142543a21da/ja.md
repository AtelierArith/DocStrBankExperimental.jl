# PublicAPI

[![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://juliaexperiments.github.io/PublicAPI.jl/dev/)

**注意**: これは、[Feature request: `Base.@public` macro for declaring a public name without needing to `export` it · Issue #42117 · JuliaLang/julia](https://github.com/JuliaLang/julia/issues/42117) の概念実証実装です。

PublicAPI.jlは、名前を`export`せずにAPIを宣言するためのシンプルなAPIを提供します：

```Julia
using PublicAPI: @public
@public public_api_name
public_api_name() = 1

export exported_and_public_api_name
exported_and_public_api_name() = 2
```

パブリックAPIは`PublicAPI.of(module)`を使用してクエリできます。たとえば、PublicAPI.jlのパブリックAPIは次のようにリストできます：

```jldoctest README
julia> using PublicAPI

julia> apis = PublicAPI.of(PublicAPI);

julia> sort!(fullname.(apis))
3-element Vector{Tuple{Symbol, Symbol}}:
 (:PublicAPI, Symbol("@public"))
 (:PublicAPI, Symbol("@strict"))
 (:PublicAPI, :of)
```

パブリックAPIの消費者は、`PublicAPI.@strict`を介して`using`の厳密な意味論を選択できます。

```Julia
import PublicAPI
PublicAPI.@strict using Upstream: api
```

これにより、`Upstream.api`が`export`されているか、`@public`としてマークされていることが保証されます。
