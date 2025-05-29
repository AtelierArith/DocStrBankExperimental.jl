```
Mder_NEP(n,Mder_fun; maxder=max)
```

Creates a `NEP` from its `compute_Mder` function defined by the function handle `Mder_fun`. The `Mder_fun(λ,der)` takes two parameters a scalar `λ::Number`, derivative number  `der`. The size `n::Int` must also be specified. The function `Mder_fun(λ,der)` should return the n x n matrix corresponding to the  `der`th derivatve. If only a limited number of derivatives are available, `maxder` should be set, e.g., if not derivatives are implemented, set `maxder=0`. The function `compute_Mlicomb` is automatically available by (delegation) to `compute_Mlincomb_from_Mder`.

Note: This is a convenience function it is not recommended for high performance computations, since, e.g., it will not maintain type stability.

# Example

The following example defines a linear eigenvalue problem `A0+λA1` defined in an external function.

```julia-repl
julia> using LinearAlgebra; # For the I function
julia> function my_Mder(s,der)
    A0=ones(Float64,3,3)-I; A0[1,1]=-1;
    A1=ones(Float64,3,3)*3; A1[2,3]=0;
    if (der==0)
       return A0+A1*s;
    elseif (der==1)
       return A1;
    else
       return zero(A0);
    end
end
julia> nep=Mder_NEP(3,my_Mder);
julia> (λ,v)=augnewton(nep,v=ones(3));
julia> norm(compute_Mder(nep,λ)*v)
5.551115123125783e-17
```
