```
reccurence_first_coef(B::Type{<:AbstractMultipleOrthogonalBasis}, degree::Integer)
```

Return `a_{degree}` in recurrence equation

$$
d_k p_k(x_i) = (a_k x_i + b_k) p_{k-1}(x_i) + c_k p_{k-2}(x_i)
$$
