```
restrict(α::DecisionDiagram, var::Int, value::Bool=true)
```

Returns the canonical form of the function α constrained at variable var=value.

# Example

```julia
x, y = variable(1), variable(2)
f = (one(x)-x)*(one(y)-1) + x*y
g = Terminal(4)*(one(x)-x) + Terminal(2)*x
h = f + g
r1 = restrict(h,1,false)
r2 = h | (2 => true) # shorthand for restrict(h,2,true)
r3 = h | (y => true) # same as above
```
