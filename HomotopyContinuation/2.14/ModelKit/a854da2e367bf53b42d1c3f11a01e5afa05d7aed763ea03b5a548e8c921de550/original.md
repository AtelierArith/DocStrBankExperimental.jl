```
dense_poly(vars::AbstractVector{Variable}, d::Integer;
           homogeneous = false,
           coeff_name::Symbol = gensym(:c))
```

Create a dense polynomial of degree `d` in the given variables `variables` where each coefficient is a parameter. Returns a tuple with the first argument being the polynomial and the second the parameters.

```julia-repl
julia> @var x y;

julia> f, c = dense_poly([x, y], 2, coeff_name = :q);

julia> f
 q₆ + x*q₄ + x^2*q₁ + y*q₅ + y^2*q₃ + x*y*q₂

julia> c
6-element Array{Variable,1}:
 q₁
 q₂
 q₃
 q₄
 q₅
 q₆
```
