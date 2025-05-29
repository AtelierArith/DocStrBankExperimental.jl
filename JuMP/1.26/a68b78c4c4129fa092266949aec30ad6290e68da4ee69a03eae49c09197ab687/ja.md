```
struct VectorConstraint
```

ベクトル制約のデータ。

JuMPの制約の表現に関する[ドキュメント](@ref)も参照してください。

## フィールド

  * `func`: フィールドには関数を表すJuMPオブジェクトが含まれます。
  * `set`: フィールドにはMOIセットが含まれます。
  * `shape`: フィールドには制約が構築された形式に一致する[`AbstractShape`](@ref)が含まれます（例えば、行列やフラットベクトルを使用して）。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:3]);

julia> @constraint(model, c, x in SecondOrderCone())
c : [x[1], x[2], x[3]] ∈ MathOptInterface.SecondOrderCone(3)

julia> object = constraint_object(c)
VectorConstraint{VariableRef, MathOptInterface.SecondOrderCone, VectorShape}(VariableRef[x[1], x[2], x[3]], MathOptInterface.SecondOrderCone(3), VectorShape())

julia> typeof(object)
VectorConstraint{VariableRef, MathOptInterface.SecondOrderCone, VectorShape}

julia> object.func
3-element Vector{VariableRef}:
 x[1]
 x[2]
 x[3]

julia> object.set
MathOptInterface.SecondOrderCone(3)

julia> object.shape
VectorShape()
```
