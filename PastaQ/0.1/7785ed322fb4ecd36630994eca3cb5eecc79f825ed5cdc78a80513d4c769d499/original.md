```
qudits(n::Int; dim::Int = 3)
qudits(d⃗::Vector)
```

Generate a $n$-qudit Hilbert space spanned by a basis $\{\sigma_j\}_{j=1}^n$. Each local degree of freedom is represented by an `ITensors.Index` object with dimension $d_j$. Accepted inputs are either the number of qudits (with the same local dimension $d$), or a vector of local dimensions $\mathrm{d}=(d_1,\dots,d_n)$.

```julia
q = qudits([3,5,3])
# 3-element Vector{ITensors.Index{Int64}}:
#  (dim=3|id=639|"Qudit,Site,n=1")
#  (dim=5|id=212|"Qudit,Site,n=2")
#  (dim=3|id=372|"Qudit,Site,n=3")
```
