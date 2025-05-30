```
issuccess(code::ExitCode) -> Bool
```

このシステムの終了コードが成功した終了を表す場合は `true` を返し、それ以外の場合は `false` を返します。

# 例

```jldoctest
julia> issuccess(Sysexits.ok)
true

julia> issuccess(Sysexits.usage)
false
```
