```
Surjection{K}

Surjection{K}(u [; check = true]) where K
Surjection(u)

(surj::Surjection)(x::T) where T <: AbstractSimplex -> Linear{T}
```

型 `Surjection{K}` は、射影オペラッドにおける次数 `K` の要素を表します。

最初のコンストラクタは、`u` によって与えられる射影を返します TODO。オプションのキーワード引数 `check` が `false` に設定されている場合、`u` が実際に射影であるかどうかはチェックされません。2番目のコンストラクタは、`K` が `maximum(u; init = 0)` に設定された最初のものと同等です。

`Surjection` が単体に適用されると、結果は対応する区間カット操作になります。この評価は線形であり、マクロ `@linear` に記載されているように、キーワード引数 `coefftype`、`addto`、`coeff`、および `is_filtered` をサポートします。

関連情報としては、[`arity`](@ref)、[`deg(::Surjection)`](@ref)、[`diff(::Surjection)`](@ref)、[`SimplicialSets.is_surjection`](@ref)、[`LinearCombinations.linear_filter(::Surjection)`](@ref)、`LinearCombinations.@linear` があります。

# 例

## 射影オペラッド

```jldoctest
julia> Surjection([1, 2, 3, 1])
Surjection{3}([1, 2, 3, 1])

julia> Surjection(Int[])
Surjection{0}(Int64[])
```

## 区間カット

```jldoctest
julia> using LinearCombinations: diff, deg

julia> surj = Surjection([1, 2, 1])
Surjection{2}([1, 2, 1])

julia> x = SymbolicSimplex(:x, 2)
x[0,1,2]

julia> surj(x)
Linear{Tensor{Tuple{SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}}}, Int64} with 3 terms:
-x[0,1,2]⊗x[0,1]-x[0,1,2]⊗x[1,2]+x[0,2]⊗x[0,1,2]

julia> diff(surj(x)) == diff(surj)(x) + (-1)^deg(surj) * surj(diff(x))
true
```
