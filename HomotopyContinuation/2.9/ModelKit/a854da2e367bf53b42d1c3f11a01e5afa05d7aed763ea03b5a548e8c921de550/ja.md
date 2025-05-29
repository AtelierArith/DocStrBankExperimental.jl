```
dense_poly(vars::AbstractVector{Variable}, d::Integer;
           homogeneous = false,
           coeff_name::Symbol = gensym(:c))
```

与えられた変数 `variables` において次数 `d` の密な多項式を作成します。各係数はパラメータです。最初の引数が多項式で、2番目がパラメータのタプルを返します。

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
