```
isfailure(code::ExitCode) -> Bool
```

このシステムの終了コードが不成功の終了を表す場合は `true` を返し、それ以外の場合は `false` を返します。

# 例

```jldoctest
julia> isfailure(Sysexits.ok)
false

julia> isfailure(Sysexits.usage)
true
```
