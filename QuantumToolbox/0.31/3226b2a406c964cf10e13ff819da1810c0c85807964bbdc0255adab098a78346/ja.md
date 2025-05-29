```
struct QuantumObjectEvolution{ObjType<:QuantumObjectType,DimType<:AbstractDimensions,DataType<:AbstractSciMLOperator} <: AbstractQuantumObject{ObjType,DimType,DataType}
    data::DataType
    type::ObjType
    dimensions::DimType
end
```

任意の時間依存量子オブジェクトを表すJulia構造体です。`data`フィールドは時間依存量子オブジェクトを表す`AbstractSciMLOperator`オブジェクトです。これは次のように見ることができます。

$$
\hat{O}(t) = \sum_{i} c_i(p, t) \hat{O}_i
$$

ここで、$c_i(p, t)$はパラメータ`p`と時間`t`に依存する関数であり、$\hat{O}_i$は量子オブジェクトを形成する演算子です。

時間非依存の場合については[`QuantumObject`](@ref)を参照し、`AbstractSciMLOperator`に関する詳細は[SciML](https://docs.sciml.ai/SciMLOperators/stable/)のドキュメントを参照してください。

!!! note "`dims`プロパティ"
    与えられた`H::QuantumObjectEvolution`に対して、`H.dims`または`getproperty(H, :dims)`はその`dimensions`を整数ベクトルの型で返します。


# 例

この演算子はQuTiPの`QobjEvo`オブジェクトと同様に初期化できます。例えば、

```jldoctest qobjevo
julia> a = tensor(destroy(10), qeye(2))

Quantum Object:   type=Operator()   dims=[10, 2]   size=(20, 20)   ishermitian=false
20×20 SparseMatrixCSC{ComplexF64, Int64} with 18 stored entries:
⎡⠀⠑⢄⠀⠀⠀⠀⠀⠀⠀⎤
⎢⠀⠀⠀⠑⢄⠀⠀⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠀⠑⢄⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠀⠀⠀⠑⢄⠀⎥
⎣⠀⠀⠀⠀⠀⠀⠀⠀⠀⠑⎦

julia> coef1(p, t) = exp(-1im * t)
coef1 (generic function with 1 method)

julia> op = QobjEvo(a, coef1)

Quantum Object Evo.:   type=Operator()   dims=[10, 2]   size=(20, 20)   ishermitian=true   isconstant=false
ScalarOperator(0.0 + 0.0im) * MatrixOperator(20 × 20)
```

演算子が2つ以上ある場合は、各演算子と係数関数のセットを2要素の`Tuple`に入れ、これらの`Tuple`を大きな`Tuple`にまとめる必要があります。

```jldoctest qobjevo
julia> σm = tensor(qeye(10), sigmam())

Quantum Object:   type=Operator()   dims=[10, 2]   size=(20, 20)   ishermitian=false
20×20 SparseMatrixCSC{ComplexF64, Int64} with 10 stored entries:
⎡⠂⡀⠀⠀⠀⠀⠀⠀⠀⠀⎤
⎢⠀⠀⠂⡀⠀⠀⠀⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠂⡀⠀⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠀⠀⠂⡀⠀⠀⎥
⎣⠀⠀⠀⠀⠀⠀⠀⠀⠂⡀⎦

julia> coef2(p, t) = sin(t)
coef2 (generic function with 1 method)

julia> op1 = QobjEvo(((a, coef1), (σm, coef2)))

Quantum Object Evo.:   type=Operator()   dims=[10, 2]   size=(20, 20)   ishermitian=true   isconstant=false
(ScalarOperator(0.0 + 0.0im) * MatrixOperator(20 × 20) + ScalarOperator(0.0 + 0.0im) * MatrixOperator(20 × 20))
```

特定の時間`t`で演算子を具体化することもできます。

```jldoctest qobjevo
julia> op1(0.1)

Quantum Object:   type=Operator()   dims=[10, 2]   size=(20, 20)   ishermitian=false
20×20 SparseMatrixCSC{ComplexF64, Int64} with 28 stored entries:
⎡⠂⡑⢄⠀⠀⠀⠀⠀⠀⠀⎤
⎢⠀⠀⠂⡑⢄⠀⠀⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠂⡑⢄⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠀⠀⠂⡑⢄⠀⎥
⎣⠀⠀⠀⠀⠀⠀⠀⠀⠂⡑⎦
```

パラメータ依存の時間発展もサポートしています。

```jldoctest qobjevo
julia> coef1(p, t) = exp(-1im * p.ω1 * t)
coef1 (generic function with 1 method)

julia> coef2(p, t) = sin(p.ω2 * t)
coef2 (generic function with 1 method)

julia> op1 = QobjEvo(((a, coef1), (σm, coef2)))

Quantum Object Evo.:   type=Operator()   dims=[10, 2]   size=(20, 20)   ishermitian=true   isconstant=false
(ScalarOperator(0.0 + 0.0im) * MatrixOperator(20 × 20) + ScalarOperator(0.0 + 0.0im) * MatrixOperator(20 × 20))

julia> p = (ω1 = 1.0, ω2 = 0.5)
(ω1 = 1.0, ω2 = 0.5)

julia> op1(p, 0.1)

Quantum Object:   type=Operator()   dims=[10, 2]   size=(20, 20)   ishermitian=false
20×20 SparseMatrixCSC{ComplexF64, Int64} with 28 stored entries:
⎡⠂⡑⢄⠀⠀⠀⠀⠀⠀⠀⎤
⎢⠀⠀⠂⡑⢄⠀⠀⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠂⡑⢄⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠀⠀⠂⡑⢄⠀⎥
⎣⠀⠀⠀⠀⠀⠀⠀⠀⠂⡑⎦
```
