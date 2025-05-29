```
interpret(command::Command)
```

Translate a `Command` object into a `Cmd` that can be executed.

# Examples

```jldoctest
julia> c = Command("ls", [LongFlag("all")], [], []);

julia> cmd = interpret(c)
`ls --all`

julia> typeof(cmd)
Cmd
```
