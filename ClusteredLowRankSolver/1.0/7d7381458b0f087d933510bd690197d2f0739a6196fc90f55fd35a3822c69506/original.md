```
linearsystem_coefficientmatching(problem::Problem, monomial_basis::Vector{Vector{MPolyRingElem}}; FF=QQ)
```

Let x be the vcat of the vectorizations of the matrix variables. This function returns the matrix A and vector b such that the constraints obtained  from coefficient matching are given by the system Ax = b over the field FF, with  one constraint per monomial in monomial_basis. The problem should not contain  SampledMPolyRingElem's for this to work.
