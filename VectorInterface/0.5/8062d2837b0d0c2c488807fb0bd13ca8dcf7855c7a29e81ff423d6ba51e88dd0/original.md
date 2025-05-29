```
add!(y, x, [α::Number = One(), β::Number = One()])
```

Add `y` and `x`, or more generally construct the linear combination `y * β + x * α`, storing the result in `y`. This will error in case of incompatible scalar types or incommensurate sizes.

!!! note
    New types should only implement the four-argument version. When desired, the two- and three-argument version can be distinguished by specializing on `α` and `β` being of type `One`.


See also: [`add`](@ref) and [`add!!`](@ref)
