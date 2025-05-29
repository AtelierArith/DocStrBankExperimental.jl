```
interpret(command::Command)
```

`Command` オブジェクトを実行可能な `Cmd` に変換します。

# 例

```jldoctest
julia> c = Command("ls", [LongFlag("all")], [], []);

julia> cmd = interpret(c)
`ls --all`

julia> typeof(cmd)
Cmd
```
