```
plot_fock_distribution(
    ρ::QuantumObject{SType};
    library::Union{Val, Symbol} = Val(:Makie),
    kwargs...
) where {SType<:Union{Ket,Operator}}
```

`ρ`の[Fock状態](https://en.wikipedia.org/wiki/Fock_state)分布をプロットします。

`library`キーワード引数は使用するプロットライブラリを指定し、デフォルトは[`Makie`](https://github.com/MakieOrg/Makie.jl)です。

# 引数

  * `ρ::QuantumObject`: Fock状態分布をプロットする量子状態。
  * `library::Union{Val,Symbol}`: 使用するプロットライブラリ。デフォルトは`Val(:Makie)`です。
  * `kwargs...`: プロット関数に渡す追加のキーワード引数。詳細については特定のプロットライブラリのドキュメントを参照してください。

!!! note "最初にライブラリをインポートする"
    この関数を使用する前に、プロットライブラリを最初にインポートする必要があります。


!!! warning "型の安定性に注意!"
    型の安定性を保ちたい場合は、プロットライブラリとして`:Makie`の代わりに`Val(:Makie)`を使用することをお勧めします。詳細については[このリンク](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-value-type)と、型の安定性に関する[関連セクション](@ref doc:Type-Stability)を参照してください。

