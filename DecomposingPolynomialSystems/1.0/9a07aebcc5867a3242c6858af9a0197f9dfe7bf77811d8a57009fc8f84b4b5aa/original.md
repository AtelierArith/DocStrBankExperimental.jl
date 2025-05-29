```
scaling_symmetries(F::System)
```

Given a polynomial system `F` returns the group of scaling symmetries  of `F`. The scalings that change the parameters are considered as well.

```julia-repl
julia> @var x y a b c;

julia> F = System([x^4+a^2+1, y^2+b+c]; variables=[x, y], parameters=[a,b,c]);

julia> scaling_symmetries(F)
ScalingGroup isomorphic to ℤ × ℤ₄ × ℤ₂
 1 free scaling:
  y ↦ y*λ, b ↦ b*λ^2, c ↦ c*λ^2

 modular scalings:
  1 of order 4:
   x ↦ -im*x, y ↦ im*y, b ↦ -b, c ↦ -c
  1 of order 2:
   x ↦ -x, y ↦ -y, a ↦ -a
```
