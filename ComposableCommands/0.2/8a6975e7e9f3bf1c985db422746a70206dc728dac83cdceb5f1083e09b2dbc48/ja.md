```
interpret(commands::AndCommands)
```

`AndCommands` オブジェクトを、結合を考慮して実行可能な `Base.AndCmds` に変換します。

# 例

```jldoctest
julia> c1 = Command("ls", [], [], []);

julia> c2 = Command("pwd", [], [], []);

julia> ac = AndCommands(c1, c2);

julia> cmd = interpret(ac)
`ls` & `pwd`

julia> typeof(cmd)
Base.AndCmds
```
