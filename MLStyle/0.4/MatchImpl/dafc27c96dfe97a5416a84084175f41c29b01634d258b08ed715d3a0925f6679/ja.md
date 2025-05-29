```
@tryswitch <item> begin
    @case <pattern>
        <action>
end
```

[`@switch`](@ref)と非常に似ていますが、マッチに失敗した場合は「マッチが非網羅的」というエラーをスローするのではなく、何もしません。

これは次のように等価です。

```julia
@switch <item> begin
    @case <pattern>
        <action>
    @case _
        nothing
    end
```
