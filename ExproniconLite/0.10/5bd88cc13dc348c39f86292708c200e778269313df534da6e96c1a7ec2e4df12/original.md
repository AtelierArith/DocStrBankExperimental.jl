```
JLIfElse(ex::Expr)
```

Create a `JLIfElse` from given Julia ifelse `Expr`.

# Example

```julia
julia> ex = :(if foo(x)
             x = 1 + 1
         elseif goo(x)
             y = 1 + 2
         else
             error("abc")
         end)
:(if foo(x)
      #= REPL[41]:2 =#
      x = 1 + 1
  elseif #= REPL[41]:3 =# goo(x)
      #= REPL[41]:4 =#
      y = 1 + 2
  else
      #= REPL[41]:6 =#
      error("abc")
  end)

julia> JLIfElse(ex)
if foo(x)
    begin
        #= REPL[41]:2 =#        
        x = 1 + 1        
    end
elseif begin
    #= REPL[41]:3 =#    
    goo(x)    
end
    begin
        #= REPL[41]:4 =#        
        y = 1 + 2        
    end
else
    begin
        #= REPL[41]:6 =#        
        error("abc")        
    end
end
```
