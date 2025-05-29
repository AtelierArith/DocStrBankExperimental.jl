```
add(y, x, [α::Number = 1, β::Number = 1])
```

Add `y` and `x`, or more generally construct the linear combination `y * β + x * α`.

!!! note
    New types should only implement the four-argument version. When desired, the two- and three-argument version can be distinguished by specializing on `α` and `β` being of type `One`.


See also: [`add!`](@ref) and [`add!!`](@ref)
