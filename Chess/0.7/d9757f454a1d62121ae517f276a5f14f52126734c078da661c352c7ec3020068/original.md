```
headervalue(ghs::GameHeaders, name::String)
headervalue(g::SimpleGame, name::String)
headervalue(g::Game, name::String)
```

Looks up the value for the header with the given name.

Returns the value as a `String`, or `nothing` if no header with the provided name exists.
