```
choi_evolve(Λ :: Matrix{<:Number}, ρ :: Matrix{<:Number}) :: Matrix
choi_evolve(
    Λ :: Matrix{<:Number}, ρ :: Matrix{<:Number}, dims :: Vector{Int}
) :: Matrix
```

密度演算子 `ρ` に対して Choi 演算子 `Λ` を適用します。ここで `dims = [dim_in, dim_out]` は Choi 演算子 `Λ` の入力および出力次元を示します。量子チャネルの出力は次のように評価されます。

$$
    \rho'_B = \text{Tr}_A[\Lambda_{AB}(\rho_A^{T}\otimes \mathbb{I}_B)],
$$

ここで [`partial_trace`](@ref) は入力系に関して取られます。

!!! warning "次元の検証"
    メソッド `choi_evolve(Λ :: Matrix{<:Number}, ρ :: Matrix{<:Number})` は `Λ` または `ρ` の次元を検証しません。適切な次元が使用されていない場合、エラーが発生します。この関数は QBase.jl の型システムをバイパスし、ユーザーが引数を検証することに依存しています。

