```
Tiling(N::Int[, x::OffsetMatrix{AztecDiamonds.Edge}]; sizehint::Int = N)
```

順序 N のダイヤモンド型タイルを表します。`x` が提供されていない場合、空のタイルを表す `NONE` で初期化されます。`sizehint` キーワード引数は、タイルが成長する際の再割り当てを避けるために、`sizehint` の順序に合った大きな行列を事前に割り当てるために使用できます。

`x` のインデックスはダイヤモンド型タイルの座標を表し、1-N から N までの範囲で動作します（ただし、`x` はこれらのインデックスを含む限り、より大きくても構いません）。含まれるエッジは `UP`、`RIGHT`、または `NONE` のいずれかであり、`UP` は上にもう1つのタイルを覆う垂直タイルを表し、`RIGHT` は右にもう1つのタイルを覆う水平タイルを表します。`NONE` は、エッジがすでに下または左の別のタイルによって覆われているか、タイルがまだ完全に埋まっていないことを意味します。

```jldoctest
julia> t = Tiling(1)
Order-1 Tiling{Matrix{AztecDiamonds.Edge}}



julia> t[0, 0] = t[1, 0] = AztecDiamonds.RIGHT;

julia> t
Order-1 Tiling{Matrix{AztecDiamonds.Edge}}
🬇🬋🬋🬃
🬇🬋🬋🬃
```

充填されたタイルを構築するには、[`diamond`](@ref) と [`ka_diamond`](@ref) を参照してください。
