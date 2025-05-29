```
@trymatch <item> begin
    <pattern> => <result>
    <pattern> => <result>
end
```

[`@match`](@ref)と非常に似ていますが、マッチに失敗した場合は「マッチが不完全」というエラーをスローするのではなく、何もしません。

これは次のように等価です。

```julia
@match <item> begin
    <pattern> => <result>
    <pattern> => <result>
    _ => nothing
    end
```
