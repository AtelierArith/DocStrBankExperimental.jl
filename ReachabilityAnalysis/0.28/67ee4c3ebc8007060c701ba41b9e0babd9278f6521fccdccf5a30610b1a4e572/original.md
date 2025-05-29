```
homogenize(ivp::IVP{<:CLCCS{N,MTA,MTB,XT,UT},ST}) where {N, MTA<:AbstractMatrix{N},
    MTB<:IdentityMultiple{N}, XT<:LazySet{N}, UT<:ConstantInput{<:Singleton{N}}, ST<:LazySet{N}}
```

Transform an inhomogeneous linear initial-value problem into a homogeneous one by introducing auxiliary state variables.

### Input

  * `ivp` – initial-value problem

### Output

Homogeneous initial-value problem.

### Notes

This function transforms the canonical initial-value problem $x' = Ax + u$, $x ∈ X$ with $u(0) ∈ U = {u}$ (a singleton) into a homogeneous problem without inputs $y' = Â * y$, $y ∈ Y$.
