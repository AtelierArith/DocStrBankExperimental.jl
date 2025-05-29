```
@switch <item> begin
    @case <pattern>
        <action>
end
```

In the real use of pattern matching provided by `MLStyle`, things can sometimes becomes painful. To end this, we have [`@when`](@ref), and now even [`@switch`](@ref).

Following code is quite stupid in many aspects:

```julia
var = 1
@match x begin
    (var_, _) => begin
        var = var_
        # do stuffs
    end
end
```

Firstly, capturing in [`@match`](@ref) just shadows outer variables, but sometimes you just want to change them.

Secondly, [`@match`](@ref) is an expression, and the right side of `=>` can be only an expression, and writing a begin end there can bring bad code format.

To address these issues, we present the `@switch` macro:

```julia
julia> var = 1
1

julia> x = (33, 44)
(33, 44)

julia> @switch x begin
       @case (var, _)
           println(var)
       end
33

julia> var
33

julia> @switch 1 begin
       @case (var, _)
           println(var)
       end
ERROR: matching non-exhaustive, at #= REPL[25]:1 =#
```
