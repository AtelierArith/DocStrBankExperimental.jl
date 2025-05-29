```
ParitySymmetry(ham::AbstractHamiltonian{T}; even=true) <: AbstractHamiltonian{T}
```

すべての状態とハミルトニアン `ham` に偶数または奇数のパリティをキーワード引数 `even` によって制御して課します。ハミルトニアンのパリティ対称性が仮定されています。いくつかのハミルトニアンに対して、`ParitySymmetry` はヒルベルト空間のサイズを半分に減少させます。

`ParitySymmetry` はユニタリ変換を行い、固有値を変更せず、[`LOStructure`](@ref) を保持します。これは、基底セットを定義されたパリティを持つ状態に変更することによって達成されます。実際には、非偶数アドレス $|α⟩$ は、偶数および奇数のパリティに対してそれぞれ $\frac{1}{√2}(|α⟩ ± |ᾱ⟩)$ に置き換えられます。ここで `ᾱ == reverse(α)` です。

# 注意事項

  * この修飾子は現在、モードの奇数の数を持つ [`starting_address`](@ref) にのみ機能します。
  * 奇数のパリティの場合、基礎となるハミルトニアンの [`starting_address`](@ref) は対称であってはなりません。
  * ハミルトニアン `ham` の対称性としてパリティが存在しない場合、結果は未定義です。
  * `ParitySymmetry` は [`offdiagonals`](@ref) イテレータを修正することによって機能します。

```jldoctest
julia> ham = HubbardReal1D(BoseFS(0,2,1))
HubbardReal1D(fs"|0 2 1⟩"; u=1.0, t=1.0)

julia> size(Matrix(ham))
(10, 10)

julia> size(Matrix(ParitySymmetry(ham)))
(6, 6)

julia> size(Matrix(ParitySymmetry(ham; odd=true)))
(4, 4)

julia> eigvals(Matrix(ham))[1] ≈ eigvals(Matrix(ParitySymmetry(ham)))[1]
true
```

他にも [`TimeReversalSymmetry`](@ref) を参照してください。
