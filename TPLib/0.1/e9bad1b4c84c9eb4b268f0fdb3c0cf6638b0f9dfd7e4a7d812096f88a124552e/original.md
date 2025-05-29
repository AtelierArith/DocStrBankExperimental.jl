```
compute_ext_rays(I::Matrix{<:SemiRing}, n::Integer)
compute_ext_rays(I::Matrix{<:Number}, n::Integer, semiring=:max)
```

Computes the set of the extreme rays of a tropical cone given by the inequalities `I` in dimension `n`, see [3]. Each row of `I` contains `2n` coefficients. When written $[a_{i1} \, \dots \, a_{in} \, b_{i1} \, \dots \, b_{in}]$, they represent the tropical inequality 

$$
\max(a_{i1} + x_1, \dots, a_{in} + x_n) \geqslant \max(b_{i1} + x_1, \dots, b_{in} + x_n)
$$

If the coefficients of `I` have type `MaxPlus{T}` or `MinPlus{T}`, then the computations are done in the max-plus or min-plus tropical semirings respectively. Otherwise, you can specify wether the coefficients should be converted to the semiring `:max` or `:min`. Returns a matrix `G::Matrix{<:SemiRing}` in which every line is a tropical point generating the cone.

# References

[1] X. Allamigeon. Static analysis of memory manipulations by abstract interpretation – Algorithmics of tropical polyhedra, and application to abstract interpretation. PhD thesis. 

[2] X. Allamigeon, S. Gaubert, E. Goubault. Computing the vertices of tropical polyhedra using directed hypergraphs. Discrete & Computational Geometry, 49(2):247–279, 2013. E-print arXiv:0904.3436v4.
