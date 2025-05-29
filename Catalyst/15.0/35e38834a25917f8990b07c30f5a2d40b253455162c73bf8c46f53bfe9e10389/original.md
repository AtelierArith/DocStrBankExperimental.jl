isautonomous(rs::ReactionSystem)

Checks if a system is autonomous (i.e. no rate or equation depend on the independent variable(s)). Example:

```julia
rs1 = @reaction_system
    (p,d), 0 <--> X
end
isautonomous(rs1) # Returns `true`.

rs2 = @reaction_system
    (p/t,d), 0 <--> X
end
isautonomous(rs2) # Returns `false`.
```
