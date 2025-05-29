(P::Union{AbstractMatrix, UniformScaling}, p::HRep)

多面体を $p$ で表現されたものを $P^{-1} p$ に変換します。各半空間 $\langle a, x \rangle \le \beta$ を $\langle P^\top a, x \rangle \le \beta$ に変換し、各超平面 $\langle a, x \rangle = \beta$ を $\langle P^\top a, x \rangle = \beta$ に変換します。
