```
log(M::EssentialManifold, p, q)
```

Compute the logarithmic map on the [`EssentialManifold`](@ref) `M`, i.e. the tangent vector, whose geodesic starting from `p` reaches `q` after time 1. Here, $p=(R_{p_1},R_{p_2})$ and $q=(R_{q_1},R_{q_2})$ are elements of $SO(3)^2$. We use that any essential matrix can, up to scale, be decomposed to

$$
E = R_1^T [e_z]_{×}R_2,
$$

where $(R_1,R_2)∈SO(3)^2$. Two points in $SO(3)^2$ are equivalent iff their corresponding essential matrices are equal (up to a sign flip). To compute the logarithm, we first move `q` to another representative of its equivalence class. For this, we find $t= t_{\text{opt}}$ for which the function

$$
f(t) = f_1 + f_2, \quad f_i = \frac{1}{2} θ^2_i(t), \quad θ_i(t)=d(R_{p_i},R_z(t)R_{b_i}) \text{ for } i=1,2,
$$

where $d(⋅,⋅)$ is the distance function in $SO(3)$, is minimized. Further, the group $H_z$ acting on the left on $SO(3)^2$ is defined as

$$
H_z = \{(R_z(θ),R_z(θ))\colon θ \in [-π,π) \},
$$

where $R_z(θ)$ is the rotation around the z axis with angle $θ$. Points in $H_z$ are denoted by $S_z$. Then, the logarithm is defined as

$$
\log_p (S_z(t_{\text{opt}})q) = [\text{Log}(R_{p_i}^T R_z(t_{\text{opt}})R_{b_i})]_{i=1,2},
$$

where $\text{Log}$ is the [`logarithm`](@ref log(::Rotations, ::Any...)) on $SO(3)$. For more details see [TronDaniilidis:2017](@cite).
