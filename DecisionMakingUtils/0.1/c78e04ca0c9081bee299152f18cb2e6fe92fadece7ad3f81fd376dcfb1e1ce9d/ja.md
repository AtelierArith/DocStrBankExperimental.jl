```
FourierBasis([::Type,] num_inputs::Int, dorder::Int, iorder::Int [, full::Bool=false])
```

与えられた次数までのフーリエ特徴を生成する構造体を作成します。結合されたフーリエ特徴、例えば、 $\cos(π(3x₁ + 2x₂))$ と、非結合特徴、$[\cos(πx₁), \cos(π2x₁), …]$ は、この基底関数を使用して生成できます。dorderパラメータは、結合特徴の次数を制御します。生成される結合特徴の数は、$(\text{dorder}+1)^{\text{num\_inputs}}$ であり、dorderが増加するにつれて指数関数的に増加するため、高次元ベクトルでの使用は推奨されません。iorderパラメータは、生成される独立特徴の次数を制御します。fullパラメータは、$\sin$ と $\cos$ の両方の特徴が生成されるかどうかを決定します。falseの場合は、cos特徴のみが生成されます。

参照: [`FourierBasisBuffer`](@ref)

# 例

```jldoctest
julia> f = FourierBasis(2, 1, 2);

julia> x = [0.0, 0.5];

julia> feats = f(x)
6-element Array{Float64,1}:
  1.0
  6.123233995736766e-17
  1.0
  6.123233995736766e-17
  1.0
 -1.0

```
