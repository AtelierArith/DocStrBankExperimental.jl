```
JLFor(ex::Expr)
```

Create a `JLFor` from given Julia for loop expression.

# Example

```julia
julia> ex = @expr for i in 1:10, j in 1:j
           M[i, j] += 1
       end
:(for i = 1:10, j = 1:j
      #= REPL[3]:2 =#
      M[i, j] += 1
  end)

julia> jl = JLFor(ex)
for i in 1 : 10,
    j in 1 : j
    #= loop body =#
    begin
        #= REPL[3]:2 =#        
        M[i, j] += 1        
    end
end

julia> jl.vars
2-element Vector{Any}:
 :i
 :j

julia> jl.iterators
2-element Vector{Any}:
 :(1:10)
 :(1:j)
```
