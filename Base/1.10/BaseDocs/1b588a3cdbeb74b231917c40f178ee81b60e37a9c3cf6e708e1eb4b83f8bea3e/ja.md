```
関数
```

すべての関数の抽象型。

# 例

```jldoctest
julia> isa(+, Function)
true

julia> typeof(sin)
typeof(sin) (関数sinのシングルトン型、Functionのサブタイプ)

julia> ans <: Function
true
```
