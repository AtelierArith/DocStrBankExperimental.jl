```
visualize(<arguments>; <keyword arguments>) -> Plot
```

Make a plot from an output collected by running necessary simulations. A convenient function to run both `simulate` and `plot` together.

See also: [`visualize!`](@ref), [`simulate`](@ref), [`plot`](@ref), [`manipulate`](@ref)

# Examples

```julia-repl
julia> @system S(Controller) begin
           a(a) => a ~ accumulate(init=1)
       end;

julia> visualize(S, :time, :a; stop=5, kind=:line)
       ┌────────────────────────────────────────┐
    32 │                                       :│
       │                                      : │
       │                                     :  │
       │                                    :   │
       │                                   :    │
       │                                  :     │
       │                                 :      │
  a    │                                :       │
       │                              .'        │
       │                            .'          │
       │                          .'            │
       │                       ..'              │
       │                   ..''                 │
       │             ....''                     │
     1 │.........''''                           │
       └────────────────────────────────────────┘
       0                                        5
                      time (hr)
```
