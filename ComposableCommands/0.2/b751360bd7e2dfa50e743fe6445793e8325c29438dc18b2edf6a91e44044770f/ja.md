```
interpret(command::RedirectedCommand)
```

`RedirectedCommand` オブジェクトを、リダイレクションを考慮して実行可能な `Base.CmdRedirect` に変換します。

# 例

```jldoctest
julia> r = RedirectedCommand(Command("ls", [], [], []), "output.txt");

julia> cmd = interpret(r)
pipeline(`ls`, stdout>Base.FileRedirect("output.txt", false))

julia> typeof(cmd)
Base.CmdRedirect

julia> r = RedirectedCommand(".zshrc", Command("cat", [], [], []));

julia> cmd = interpret(r)
pipeline(`cat`, stdin<Base.FileRedirect(".zshrc", false))

julia> typeof(cmd)
Base.CmdRedirect
```
