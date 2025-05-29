```
SOS1(weights = Real[])
```

SOS1（特別順序集合タイプ1）は、ベクトル `x` を制約し、最大1つの変数が非ゼロの値を取ることができ、他のすべての要素はゼロである集合に制約します。

指定された場合、`weights` ベクトルは変数の順序を誘導します。そのため、ユニークな値を含む必要があります。`weights` ベクトルは、ベクトル `x` と同じ数の要素を持たなければならず、要素 `weights[i]` は要素 `x[i]` に対応します。提供されない場合、`weights` ベクトルはデフォルトで `weights[i] = i` になります。

これは [`MOI.SOS1`](@ref) セットのショートカットです。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:3] in SOS1([4.1, 3.2, 5.0]))
3-element Vector{VariableRef}:
 x[1]
 x[2]
 x[3]

julia> print(model)
Feasibility
Subject to
 [x[1], x[2], x[3]] ∈ MathOptInterface.SOS1{Float64}([4.1, 3.2, 5.0])
```
