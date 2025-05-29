```julia
project!(
    state::QuantumClifford.MixedStabilizer,
    pauli::QuantumClifford.PauliOperator;
    phases
) -> Tuple{QuantumClifford.MixedStabilizer, Int64, Any}

```

[`project!`](@ref) を [`MixedStabilizer`](@ref) に使用すると、混合状態を表すために `Stabilizer` データ構造を暗黙的に使用する際に遭遇するいくつかの追加ステップを自動化します。具体的には、プロジェクターが安定器のリストに含まれていない場合に役立ちます：

```jldoctest
julia> s = S"XZI
             IZI";


julia> ms = MixedStabilizer(s)
+ X__
+ _Z_

julia> project!(ms, P"IIY")[1]
+ X__
+ _Z_
+ __Y
```

[`Stabilizer`](@ref) に対する [`project!`](@ref) と同様に、この関数はパウリ演算子が表のすべての行と可換である場合に立方体の複雑さを持ちます。ほとんどの場合、単に [`MixedDestabilizer`](@ref) 表現を使用する方が良いです。

他の `project!` メソッドとは異なり、このメソッドは `keep_result=false` を許可しません。なぜなら、正しいランクまたは反交換インデックスは、`keep_result=true` に必要な高価な（立方体の）標準化操作なしでは計算できないからです。

詳細については、ドキュメントの「データ構造の選択」セクションを参照してください。

関連項目: [`projectX!`](@ref), [`projectY!`](@ref), [`projectZ!`](@ref).
