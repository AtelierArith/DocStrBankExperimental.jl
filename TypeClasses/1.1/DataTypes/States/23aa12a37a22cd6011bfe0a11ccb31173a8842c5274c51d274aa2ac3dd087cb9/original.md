```
getstate
```

Standard value for returning the hidden state of the `State` Monad.

## Examples

```jldoctest
julia> using TypeClasses

julia> mystate = @syntax_flatmap begin
         state = getstate
         @pure println("state = $state")
       end;

julia> mystate(42)
state = 42
(nothing, 42)
```
