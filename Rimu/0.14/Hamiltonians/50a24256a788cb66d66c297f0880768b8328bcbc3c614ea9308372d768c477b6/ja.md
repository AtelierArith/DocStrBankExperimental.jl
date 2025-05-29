```
dimension(h::AbstractHamiltonian, addr=starting_address(h))
dimension(h::AbstractObservable, addr)
dimension(addr::AbstractFockAddress)
dimension(::Type{<:AbstractFockAddress})
```

ヒルベルト空間の推定次元を返します。`BigInt` 数を返すことがあります。

アドレスまたはアドレスタイプに対して呼び出された場合、アドレスタイプによって張られる線形空間の次元が返されます。`AbstractHamiltonian` に対して呼び出された場合、ハミルトニアンを表す行列の次元の上限が返されます。

# 例

```jldoctest
julia> dimension(OccupationNumberFS(1,2,3))
16777216

julia> dimension(HubbardReal1D(OccupationNumberFS(1,2,3)))
28

julia> dimension(BoseFS{200,100})
1386083821086188248261127842108801860093488668581216236221011219101585442774669540

julia> Float64(ans)
1.3860838210861882e81
```

[`AbstractHamiltonian`](@ref) インターフェースの一部です。 [`BasisSetRepresentation`](@ref) も参照してください。

# 拡張ヘルプ

[`AbstractHamiltonian`](@ref) に対して呼び出された `dimension` のデフォルトフォールバックは、アドレス空間の次元を返すことで、上限を提供します。新しいハミルトニアンの場合、カスタムメソッドを定義することで、より厳密な上限を提供できます。

[`AbstractHamiltonian`](@ref) を拡張する際は、二引数形式 `dimension(h::MyNewHamiltonian, addr)` のメソッドを定義してください。数保存ハミルトニアンの場合、関数 [`Hamiltonians.number_conserving_dimension`](@ref) が役立つかもしれません。

[`AbstractFockAddress`](@ref) を拡張する際は、`dimension(::Type{MyNewFockAddress})` のメソッドを定義してください。
