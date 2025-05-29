(P::Union{AbstractMatrix, UniformScaling}, p::HRep)

Transform the polyhedron represented by $p$ into $P^{-1} p$ by transforming each halfspace $\langle a, x \rangle \le \beta$ into $\langle P^\top a, x \rangle \le \beta$ and each hyperplane $\langle a, x \rangle = \beta$ into $\langle P^\top a, x \rangle = \beta$.
