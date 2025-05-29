```
point_ordering!(B::BracketAlgebra, point_ordering::AbstractVector{<:Integer}=collect(1:B.n))
```

Update the point ordering of the bracket algebra `B` to `point_ordering` and return the updated bracket algebra.

Warning: changing the point ordering will not change the representation of already generated elements of `B`, which leads to wrong results when working with these elements. It is recommended to create a new bracket algebra with the desired point ordering instead. 

# Examples

```jldoctest
julia> point_ordering!(BracketAlgebra(6,3), [6,5,4,3,2,1])
Bracket algebra over P^3 on 6 points with point ordering 6 < 5 < 4 < 3 < 2 < 1 and coefficient ring Integers.
```
