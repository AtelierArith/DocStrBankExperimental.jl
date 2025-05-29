```
MOInput(x::AbstractVector, out_dim::Integer)
```

多次元出力データのモデリングに対応するデータ型です。`MOInput(x, out_dim)`は長さ`length(x) * out_dim`を持ちます。

```jldoctest
julia> x = [1, 2, 3];

julia> MOInput(x, 2)
6-element KernelFunctions.MOInputIsotopicByOutputs{Int64, Vector{Int64}, Int64}:
 (1, 1)
 (2, 1)
 (3, 1)
 (1, 2)
 (2, 2)
 (3, 2)
```

上記のように、`MOInput`はタプルのベクトルを表します。最初の`length(x)`要素は最初の出力の入力を表し、2番目の`length(x)`要素は2番目の出力の入力を表します。詳細については、ドキュメントの[Inputs for Multiple Outputs](@ref)を参照してください。

`MOInput`は、`MOInputIsotopicByOutputs`に代わってバージョン0.11で非推奨となり、バージョン0.12で削除されます。
