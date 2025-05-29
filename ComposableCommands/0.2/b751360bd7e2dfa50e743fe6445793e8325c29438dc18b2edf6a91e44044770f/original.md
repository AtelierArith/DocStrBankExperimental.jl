```
interpret(command::RedirectedCommand)
```

Translate a `RedirectedCommand` object into a `Base.CmdRedirect` that can be executed, considering the redirection.

# Examples

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
