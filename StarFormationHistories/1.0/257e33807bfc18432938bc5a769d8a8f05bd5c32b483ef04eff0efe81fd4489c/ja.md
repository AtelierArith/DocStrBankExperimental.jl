```
LogarithmicAMR(constraint1, constraint2, T_max::Real=137//10,
               MH_func = MH_from_Z, dMH_dZ = dMH_dZ, Z_func = Z_from_MH,
               free::NTuple{2, Bool}=(true, true))
```

MH制約を持つ`LogarithmicAMR`のインスタンスを、2つの異なるルックバック時間から構築します。`constraint1`と`constraint2`の各々は、最初の要素が金属量 [M/H] で、2番目の要素がGyr単位のルックバック時間である長さ2のインデックス可能なオブジェクト（例えば、タプル）である必要があります。制約の順序は重要ではありません。

# 例

```jldoctest; setup = :(import StarFormationHistories: LogarithmicAMR)
julia> LogarithmicAMR((-2.5, 13.7), (-1.0, 0.0), 13.7) isa LogarithmicAMR{Float64}
true

julia> LogarithmicAMR((-2.5, 13.7), (-1.0, 0.0), 13.7) ==
           LogarithmicAMR((-1.0, 0.0), (-2.5, 13.7), 13.7)
true
```
