```
interpret(commands::AndCommands)
```

Translate an `AndCommands` object into a `Base.AndCmds` that can be executed, considering the conjunction.

# Examples

```jldoctest
julia> c1 = Command("ls", [], [], []);

julia> c2 = Command("pwd", [], [], []);

julia> ac = AndCommands(c1, c2);

julia> cmd = interpret(ac)
`ls` & `pwd`

julia> typeof(cmd)
Base.AndCmds
```
