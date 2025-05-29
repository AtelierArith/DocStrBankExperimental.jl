```
precond!(re::RE, s::Symbol; [when=:enter], [bool=true]) -> re
```

Set `re`'s precondition to `s`. Before any state transitions to `re`, or inside `re`, the precondition code `s` is checked to be `bool` before the transition is taken.

`when` controls if the condition is checked when the regex is entered (if `:enter`), or at every state transition inside the regex (if `:all`)

# Example

```julia
julia> regex = re"ab?c*";

julia> regex2 = precond!(regex, :some_condition);

julia> regex === regex2
true
```
