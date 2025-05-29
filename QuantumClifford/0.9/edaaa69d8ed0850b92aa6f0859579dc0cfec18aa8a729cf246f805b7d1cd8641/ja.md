「シンボリック」な一般的な単一量子ビット演算子で、明示的なタブローとして表現された演算子よりも高速な乗算を可能にします。

```jldoctest
julia> op = SingleQubitOperator(2, true, true, true, false, true, true) # タブローのコンポーネントと位相
SingleQubitOperator on qubit 2
X₁ ⟼ - Y
Z₁ ⟼ - X

julia> typeof(op)
SingleQubitOperator

julia> t_op = CliffordOperator(op, 3) # 明示的なタブロー表現に戻す（サイズを指定）
X₁ ⟼ + X__
X₂ ⟼ - _Y_
X₃ ⟼ + __X
Z₁ ⟼ + Z__
Z₂ ⟼ - _X_
Z₃ ⟼ + __Z

julia> typeof(t_op)
CliffordOperator{QuantumClifford.Tableau{Vector{UInt8}, Matrix{UInt64}}, PauliOperator{Array{UInt8, 0}, Vector{UInt64}}}

julia> CliffordOperator(op, 1, compact=true) # タブローの非自明な部分だけを抽出することもできます
X₁ ⟼ - Y
Z₁ ⟼ - X
```

参照: [`sHadamard`](@ref), [`sPhase`](@ref), [`sId1`](@ref), [`sX`](@ref), [`sY`](@ref), [`sZ`](@ref), [`CliffordOperator`](@ref)

または、`subtypes(QuantumClifford.AbstractSingleQubitOperator)` と `subtypes(QuantumClifford.AbstractTwoQubitOperator)` を参照して完全なリストを確認できます。`s` プレフィックスは「シンボリック」または「スパース」と考えることができます。
