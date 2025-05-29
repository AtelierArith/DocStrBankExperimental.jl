```
kernel(A::MatElem; side::Symbol = :left)
kernel(C::SolveCtx; side::Symbol = :left)
```

Return a matrix $K$ whose rows generate the left kernel of $A$, that is, $KA$ is the zero matrix.

If `side == :right`, the columns of $K$ generate the right kernel of $A$, that is, $AK$ is the zero matrix.

If the base ring is a principal ideal domain, the rows or columns respectively of $K$ are a basis of the respective kernel.

If a context object `C` is supplied, then the above applies for `A = matrix(C)`.

#Example

```jldoctest
julia> A = QQ[2 6 0 0;1 3 0 0;0 0 5 0];

julia> kernel(A, side=:right)
[-3//1   0//1]
[ 1//1   0//1]
[ 0//1   0//1]
[ 0//1   1//1]

julia> kernel(A)
[-1//2   1//1   0//1]
```
