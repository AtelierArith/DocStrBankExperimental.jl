# DefineSingletons

[![GitHub Actions](https://github.com/tkf/DefineSingletons.jl/workflows/Run%20tests/badge.svg)](https://github.com/tkf/DefineSingletons.jl/actions?query=workflow%3A%22Run+tests%22)

シングルトンとそのプリティプリント `show` を一度に定義します：

```jldoctest README
julia> using DefineSingletons

julia> @def_singleton mysingleton;

julia> mysingleton
mysingleton

julia> Base.issingletontype(typeof(mysingleton))
true
```

`@def_singleton` のドキュメント文字列で詳細を確認してください。
