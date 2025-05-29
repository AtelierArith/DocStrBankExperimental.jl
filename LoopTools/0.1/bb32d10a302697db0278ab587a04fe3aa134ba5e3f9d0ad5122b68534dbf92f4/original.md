```
eput!(res::Vector{ComplexF64}, p1^2, p2^2, p3^2, p4^2, p5^2, (p1+p2)^2, 
(p2+p3)^2, (p3+p4)^2, (p4+p5)^2, (p5+p1)^2, m1^2, m2^2, m3^2, m4^2, m5^2)
```

return all five-point coefficients to the preallocated array `res` of length 258.

See also [`eget`](@ref) and [`egetsym`](@ref).
