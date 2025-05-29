```
TimeReversalSymmetry(ham::AbstractHamiltonian{T}; even=true) <: AbstractHamiltonian{T}
```

すべての状態とハミルトニアン `ham` に対して、キーワード引数 `even` によって制御される偶数または奇数の時間反転を課します。時間反転がハミルトニアンの対称性である場合、これはブロック（ヒルベルト空間の次元を減少させる）し、固有値と [`LOStructure`](@ref) を保持します。

# 注意事項

  * この修飾子は二成分の [`starting_address`](@ref) にのみ機能します。
  * 奇数の時間反転対称性の場合、基礎となるハミルトニアンの [`starting_address`](@ref) は対称であってはなりません。
  * 時間反転がハミルトニアン `ham` の対称性でない場合、結果は未定義です。
  * `TimeReversalSymmetry` は [`offdiagonals`](@ref) イテレータを修正することによって機能します。

```jldoctest
julia> ham = HubbardMom1D(FermiFS2C((1,0,1),(0,1,1)));

julia> size(Matrix(ham))
(3, 3)

julia> size(Matrix(TimeReversalSymmetry(ham)))
(2, 2)

julia> size(Matrix(TimeReversalSymmetry(ham, even=false)))
(1, 1)

julia> eigvals(Matrix(TimeReversalSymmetry(ham)))[1] ≈ eigvals(Matrix(ham))[1]
true
```

他にも [`ParitySymmetry`](@ref) を参照してください。
