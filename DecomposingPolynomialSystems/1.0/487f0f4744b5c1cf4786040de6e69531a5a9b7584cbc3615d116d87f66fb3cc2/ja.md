```
symmetries_fixing_parameters(F::System; degree_bound=1, param_dep=true, kwargs...)
```

多項式系 F に対して、パラメータを固定する F の対称群を返します。キーワード引数 `degree_bound` は、対称性の表現における分子および分母多項式の次数の上限を設定するために使用されます。`param_dep` キーワード引数は、対称性の関数が F のパラメータに依存するかどうかを指定します。

```julia-repl
julia> @var x[1:2] p[1:2];

julia> F = System([x[1]^2 - x[2]^2 - p[1], 2*x[1]*x[2] - p[2]]; variables=x, parameters=p);

julia> symmetries_fixing_parameters(F; degree_bound=1, param_dep=false)
DeckTransformationGroup of order 4
 structure: C2 x C2
 action:
  1st map:
   x₁ ↦ x₁
   x₂ ↦ x₂
  2nd map:
   x₁ ↦ -x₁
   x₂ ↦ -x₂
  3rd map:
   x₁ ↦ im*x₂
   x₂ ↦ -im*x₁
  4th map:
   x₁ ↦ -im*x₂
   x₂ ↦ im*x₁
```
