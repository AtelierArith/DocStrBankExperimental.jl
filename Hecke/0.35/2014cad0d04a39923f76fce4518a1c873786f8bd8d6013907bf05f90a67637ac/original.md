```
kernel_lattice(L::ZZLat, f::MatElem;
               ambient_representation::Bool = true) -> ZZLat
```

Given a $\mathbf{Z}$-lattice $L$ and a matrix $f$ inducing an endomorphism of $L$, return $\ker(f)$ is a sublattice of $L$.

If `ambient_representation` is `true` (the default), the endomorphism is represented with respect to the ambient space of $L$. Otherwise, the endomorphism is represented with respect to the basis of $L$.
