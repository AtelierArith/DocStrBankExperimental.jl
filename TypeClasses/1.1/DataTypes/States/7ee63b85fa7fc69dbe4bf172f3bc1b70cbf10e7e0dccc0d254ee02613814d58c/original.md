```
putstate(x)
```

`putstate` is a standard constructor for `State` objects which changes the underlying state to the given value. 

## Examples

```jldoctest
julia> using TypeClasses

julia> mystate = @syntax_flatmap begin
         putstate(10)
         state = getstate
         @pure println("The state is $state, and should be 10")
       end;

julia> mystate()
The state is 10, and should be 10
(nothing, 10)
```
