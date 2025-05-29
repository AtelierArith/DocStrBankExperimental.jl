```
interpret(commands::OrCommands)
```

`OrCommands` オブジェクトを、選言を考慮して実行可能な `Base.OrCmds` に変換します。

# 例

```jldoctest
julia> c1 = Command("ls", [], [], []);

julia> c2 = Command("pwd", [], [], []);

julia> oc = OrCommands(c1, c2);

julia> cmd = interpret(oc)
pipeline(`ls`, stdout=`pwd`)

julia> typeof(cmd)
Base.OrCmds
```
