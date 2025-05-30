```
parentmodule(t::DataType) -> Module
```

定義されている（潜在的に `UnionAll` でラップされた） `DataType` を含むモジュールを特定します。

# 例

```jldoctest
julia> module Foo
           struct Int end
       end
Foo

julia> parentmodule(Int)
Core

julia> parentmodule(Foo.Int)
Foo
```
