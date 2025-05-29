```
invariant_lattice(L::ZZLat, G::Vector{MatElem};
                  ambient_representation::Bool = true) -> ZZLat
invariant_lattice(L::ZZLat, G::MatElem;
                  ambient_representation::Bool = true) -> ZZLat
```

Given a $\mathbf{Z}$-lattice $L$ and a list of matrices $G$ inducing endomorphisms of $L$ (or just one matrix $G$), return the lattice $L^G$, consisting on elements fixed by $G$.

If `ambient_representation` is `true` (the default), the endomorphism is represented with respect to the ambient space of $L$. Otherwise, the endomorphism is represented with respect to the basis of $L$.
