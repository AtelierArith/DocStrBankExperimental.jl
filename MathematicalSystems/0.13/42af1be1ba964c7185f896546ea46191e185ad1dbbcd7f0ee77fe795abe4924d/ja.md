```
InitialValueProblem{S <: AbstractSystem, XT} <: AbstractSystem
```

初期値問題のためのパラメトリック合成型。システムの型と初期状態の型でパラメータ化されています。

### フィールド

  * `s`  – システム
  * `x0` – 初期状態

### 例

初期条件 $x₀ = [-1/2, 1/2]$ を持つ線形システム $x' = -x$:

```jldoctest
julia> s = LinearContinuousSystem([-1.0 0.0; 0.0 -1.0]);

julia> x₀ = [-1/2, 1/2];

julia> p = InitialValueProblem(s, x₀);

julia> initial_state(p) # p.x0 と同じ
2-element Vector{Float64}:
 -0.5
  0.5

julia> statedim(p)
2

julia> inputdim(p)
0
```
