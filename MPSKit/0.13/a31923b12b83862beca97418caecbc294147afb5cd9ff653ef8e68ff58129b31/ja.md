```
expectation_value(ψ, O, [environments])
expectation_value(ψ, inds => O)
```

演算子 `O` の期待値を状態 `ψ` に対して計算します。オプションとして、以前に計算された `environments` を渡すことで計算をより効率的にすることが可能です。

一般に、演算子 `O` はすべてのサイトに作用する任意のMPO `O <: AbstractMPO` であるか、またはサイトのサブセットに作用するローカル演算子 `O = inds => operator` である可能性があります。後者の場合、`inds` は演算子が作用するサイトを指定するインデックスのタプルであり、演算子は `AbstractTensorMap` または `FiniteMPO` である必要があります。

# 引数

  * `ψ::AbstractMPS` : 期待値を計算する状態
  * `O::Union{AbstractMPO,Pair}` : 期待値を計算する演算子。これは `AbstractMPO` であるか、インデックスとローカル演算子のペアである必要があります。
  * `environments::AbstractMPSEnvironments` : 計算に使用する環境。指定されていない場合は、計算されます。

# 例

```jldoctest
julia> ψ = FiniteMPS(ones(Float64, (ℂ^2)^4));

julia> S_x = TensorMap(Float64[0 1; 1 0], ℂ^2, ℂ^2);

julia> round(expectation_value(ψ, 2 => S_x))
1.0

julia> round(expectation_value(ψ, (2, 3) => S_x ⊗ S_x))
1.0
```
