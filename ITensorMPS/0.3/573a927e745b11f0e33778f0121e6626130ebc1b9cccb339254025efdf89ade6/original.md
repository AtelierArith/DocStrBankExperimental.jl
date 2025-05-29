```
error_contract(y::MPS, A::MPO, x::MPS;
               make_inds_match::Bool = true)
error_contract(y::MPS, x::MPS, A::MPO;
               make_inds_match::Bool = true)
```

Compute the distance between A|x> and an approximation MPS y: `| |y> - A|x> |/| A|x> | = √(1 + (<y|y> - 2*real(<y|A|x>))/<Ax|A|x>)`.

If `make_inds_match = true`, the function attempts match the site indices of `y` with the site indices of `A` that are not common with `x`.
