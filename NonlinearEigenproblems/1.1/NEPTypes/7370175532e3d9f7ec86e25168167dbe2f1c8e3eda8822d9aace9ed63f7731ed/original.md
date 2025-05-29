```
Mder_Mlincomb_NEP(n,Mder_fun, [maxder_Mder,] Mlincomb_fun, [maxder_Mlincomb])
```

Creates a `NEP` from its `compute_Mder` and `compute_Mlincomb`functions  defined by the function handles `Mder_fun` and `Mlincomb_fun`. The `Mlincomb_fun(λ,X)` takes two parameters a scalar `λ::Number` and a matrix `X`.  The size `n::Int` must also be specified. The function `Mlincomb_fun(λ,X)` should return a vector corresponding of the linear combination of derivatives multiplied with the vectors in X. If only a limited number of derivatives are implemented, `maxder_Mder` or `maxder_Mlincomb` should be set, e.g., if not derivatives are implemented, set `maxder=0`.

See also `Mder_NEP`.

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
julia> function my_Mlincomb(s,X) # Compute linear comb of derivatives
    A0=ones(Float64,3,3)-I; A0[1,1]=-1;
    A1=ones(Float64,3,3)*3; A1[2,3]=0;
    if (size(X,2) <= 1)
       return A0*X[:,1]+s*A1*X[:,1]
    else # This means: size(X,2) => 2
       return A0*X[:,1]+A1*(s*X[:,1]+X[:,2]);
    end
end
julia> nep=Mder_Mlincomb_NEP(3,my_Mder,my_Mlincomb);
julia> (λ,v)=augnewton(nep,v=[1.0; 2.3; 0.0])
julia> norm(compute_Mder(nep,λ)*v)
6.798699777552591e-17
```
