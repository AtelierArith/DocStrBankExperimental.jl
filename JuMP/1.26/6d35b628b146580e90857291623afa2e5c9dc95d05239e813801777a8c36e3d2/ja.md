```
SOS2(weights = Real[])
```

SOS2（特別順序集合タイプ2）は、ベクトル `x` を制約し、最大2つの変数が非ゼロの値を取ることができ、他のすべての要素はゼロである集合に制約します。さらに、2つの非ゼロの値は、`weights` によって誘導される `x` ベクトルの順序に従って連続している必要があります。

`weights` ベクトルは、指定されている場合、変数の順序を誘導します。そのため、ユニークな値を含む必要があります。`weights` ベクトルは、ベクトル `x` と同じ数の要素を持たなければならず、要素 `weights[i]` は要素 `x[i]` に対応します。提供されない場合、`weights` ベクトルはデフォルトで `weights[i] = i` になります。

これは [`MOI.SOS2`](@ref) セットのショートカットです。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:3] in SOS2([4.1, 3.2, 5.0]))
3-element Vector{VariableRef}:
 x[1]
 x[2]
 x[3]

julia> print(model)
Feasibility
Subject to
 [x[1], x[2], x[3]] ∈ MathOptInterface.SOS2{Float64}([4.1, 3.2, 5.0])
```
