```
is_invertible_with_inverse(A::MatrixElem{T}; side::Symbol = :left) where {T <: RingElement}
```

Given an $n \times m$ matrix $A$ over a ring, return a tuple `(flag, B)`. If `side` is `:right` and `flag` is `true`, $B$ is a right inverse of $A$ i.e. $A B$ is the $n \times n$ unit matrix. If `side` is `:left` and `flag` is `true`, $B$ is a left inverse of $A$ i.e. $B A$ is the $m \times m$ unit matrix. If `flag` is `false`, no right or left inverse exists.

To get the space of all inverses, note that if $B$ and $C$ are both right inverses, then $A (B - C) = 0$, and similar for left inverses. Hence from one inverse one can find all by making suitable use of [`kernel`](@ref).
