```
command!(
    f::Function
    c::Client
    name::AbstractString
    description::AbstractString;
    kwargs...
)
```

Adds a handler for INTERACTION CREATE gateway events where the InteractionData's `name` field matches `name`. Adds this command to `c.commands` or `c.guild_commands` based on the presence of `guild`. The `f` parameter signature should be:

```
    (ctx::Context, args...) -> Any 
```

Where args is a list of all the Command Options

For example a command that takes a user u and a number n as input should have this signature:

```
(ctx::Context, u::User, n::Int) -> Any
```

and the arguments would automatically get converted.

**Note:** The argument names **must** match the Option names. The arguments can be ordered in any way. If no type is specified, no conversion will be performed, so Discord objects will be `Snowflake`s.
