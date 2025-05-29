```
(A::QuantumObjectEvolution)(ψout, ψin, p, t)
```

時間依存の [`QuantumObjectEvolution`](@ref) オブジェクト `A` を、パラメータ `p` で時刻 `t` における入力状態 `ψin` に適用します。出力状態は `ψout` に格納されます。この関数は `AbstractSciMLOperator` オブジェクトの動作を模倣します。

# 引数

  * `ψout::QuantumObject`: 出力状態。`ψin` と同じ型でなければなりません。
  * `ψin::QuantumObject`: 入力状態。`[`Ket`](@ref)` または `[`OperatorKet`](@ref)` のいずれかでなければなりません。
  * `p`: 時間依存の係数のパラメータ。
  * `t`: 係数が評価される時刻。

# 戻り値

  * `ψout::QuantumObject`: 出力状態。

# 例

```jldoctest
julia> a = destroy(20)

Quantum Object:   type=Operator()   dims=[20]   size=(20, 20)   ishermitian=false
20×20 SparseMatrixCSC{ComplexF64, Int64} with 19 stored entries:
⎡⠈⠢⡀⠀⠀⠀⠀⠀⠀⠀⎤
⎢⠀⠀⠈⠢⡀⠀⠀⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠈⠢⡀⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠀⠀⠈⠢⡀⠀⎥
⎣⠀⠀⠀⠀⠀⠀⠀⠀⠈⠢⎦

julia> coef1(p, t) = sin(t)
coef1 (generic function with 1 method)

julia> coef2(p, t) = cos(t)
coef2 (generic function with 1 method)

julia> A = QobjEvo(((a, coef1), (a', coef2)))

Quantum Object Evo.:   type=Operator()   dims=[20]   size=(20, 20)   ishermitian=true   isconstant=false
(ScalarOperator(0.0 + 0.0im) * MatrixOperator(20 × 20) + ScalarOperator(0.0 + 0.0im) * MatrixOperator(20 × 20))

julia> ψ1 = fock(20, 3);

julia> ψ2 = zero_ket(20);

julia> A(ψ2, ψ1, nothing, 0.1) ≈ A(0.1) * ψ1
true
```
