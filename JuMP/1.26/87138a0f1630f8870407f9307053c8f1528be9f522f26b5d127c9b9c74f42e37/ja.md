```
HermitianPSDCone
```

エルミート正半定値円錐オブジェクトで、[`@variable`](@ref)および[`@constraint`](@ref)マクロを使用してエルミート正半定値の正方行列を作成するために使用できます。

## 例

次の例を考えてみましょう：

```jldoctest
julia> model = Model();

julia> @variable(model, H[1:3, 1:3] in HermitianPSDCone())
3×3 LinearAlgebra.Hermitian{GenericAffExpr{ComplexF64, VariableRef}, Matrix{GenericAffExpr{ComplexF64, VariableRef}}}:
 real(H[1,1])                    …  real(H[1,3]) + imag(H[1,3]) im
 real(H[1,2]) - imag(H[1,2]) im     real(H[2,3]) + imag(H[2,3]) im
 real(H[1,3]) - imag(H[1,3]) im     real(H[3,3])

julia> c = constraint_object(VariableInSetRef(H));

julia> c.func
9-element Vector{VariableRef}:
 real(H[1,1])
 real(H[1,2])
 real(H[2,2])
 real(H[1,3])
 real(H[2,3])
 real(H[3,3])
 imag(H[1,2])
 imag(H[1,3])
 imag(H[2,3])

julia> c.set
MathOptInterface.HermitianPositiveSemidefiniteConeTriangle(3)
```

最後のコマンドの出力から、9つの実数変数が作成されたことがわかります。行列 `H` は、これらの9つの変数に関してアフィン表現を制約します。これはエルミート行列をパラメータ化します。
