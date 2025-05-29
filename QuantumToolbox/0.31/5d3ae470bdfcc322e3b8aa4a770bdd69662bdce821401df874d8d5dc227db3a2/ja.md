```
plot_wigner(
    state::QuantumObject{OpType}; 
    library::Union{Val,Symbol}=Val(:Makie), 
    kwargs...
) where {OpType<:Union{Bra,Ket,Operator}
```

`state`の[ウィグナー準確率分布](https://en.wikipedia.org/wiki/Wigner_quasiprobability_distribution)をプロットするには、[`wigner`](@ref)関数を使用します。

`library`キーワード引数は、使用するプロットライブラリを指定し、デフォルトは[`Makie.jl`](https://github.com/MakieOrg/Makie.jl)です。

# 引数

  * `state::QuantumObject`: ウィグナー分布をプロットする量子状態。
  * `library::Union{Val,Symbol}`: 使用するプロットライブラリ。デフォルトは`Val(:Makie)`です。
  * `kwargs...`: プロット関数に渡す追加のキーワード引数。特定のプロットライブラリのドキュメントを参照して、詳細を確認してください。

!!! note "最初にライブラリをインポートする"
    この関数を使用する前に、プロットライブラリを最初にインポートする必要があります。


!!! warning "型の安定性に注意!"
    型の安定性を保ちたい場合は、プロットライブラリとして`:Makie`の代わりに`Val(:Makie)`を使用することをお勧めします。詳細については[このリンク](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-value-type)と、型の安定性に関する[関連セクション](@ref doc:Type-Stability)を参照してください。

