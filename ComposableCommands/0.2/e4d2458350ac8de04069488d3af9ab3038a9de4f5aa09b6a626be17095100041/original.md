```
interpret(commands::OrCommands)
```

Translate an `OrCommands` object into a `Base.OrCmds` that can be executed, considering the disjunction.

# Examples

```jldoctest
julia> c1 = Command("ls", [], [], []);

julia> c2 = Command("pwd", [], [], []);

julia> oc = OrCommands(c1, c2);

julia> cmd = interpret(oc)
pipeline(`ls`, stdout=`pwd`)

julia> typeof(cmd)
Base.OrCmds
```
