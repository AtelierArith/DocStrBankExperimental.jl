```
q = project(M::SPDFixedDeterminant, p)
project!(M::SPDFixedDeterminant, q, p)
```

Project the symmetric positive definite (s.p.d.) matrix `p` from the embedding onto the (sub-)manifold of s.p.d. matrices of determinant `M.d` (in place of `q`).

The formula reads

$$
q = \Bigl(\frac{d}{\det(p)}\Bigr)^{\frac{1}{n}}p
$$
