```
@match <item> begin
    <pattern> => <result>
    <pattern> => <result>
    _ => <other>
end
```

パターンマッチング式を定義します。利用可能なパターンは、[Patterns](https://thautwarm.github.io/MLStyle.jl/latest/syntax/pattern.html#patterns) ドキュメントのセクションで確認できます。

# 例

```julia
julia> @match 10 begin
    1  => "wrong!"
    2  => "wrong!"
    10 => "right!"
end
"right!"

julia> @match 1 begin
    ::Float64  => nothing
    b :: Int => b
    _        => nothing
end
1
```
