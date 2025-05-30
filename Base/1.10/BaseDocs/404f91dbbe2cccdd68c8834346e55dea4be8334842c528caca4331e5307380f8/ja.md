```
applicable(f, args...) -> Bool
```

与えられた引数に適用可能なメソッドを持つかどうか、指定された汎用関数を判断します。

関連情報は [`hasmethod`](@ref) を参照してください。

# 例

```jldoctest
julia> function f(x, y)
           x + y
       end;

julia> applicable(f, 1)
false

julia> applicable(f, 1, 2)
true
```
