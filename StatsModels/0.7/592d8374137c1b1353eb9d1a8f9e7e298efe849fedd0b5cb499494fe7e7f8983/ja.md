```
HypothesisCoding(hypotheses::Vector{Pair}; levels=nothing)
```

仮説を `label=>hypothesis_vector` ペアのベクターとして指定します。 ラベルはペアのキーから生成されます。 `levels` 引数は、仮説ベクターの各エントリのレベルの名前を提供します。 省略した場合、`ContrastsMatrix` を構築する際にデータに対して `levels` 関数が呼び出されます。

# 例

```jldoctest
julia> hc = HypothesisCoding(["a_and_b" => [1, 1, 0], "b_and_c" => [0, 1, 1]];
                             levels=["a", "b", "c"]);

julia> hc.hypotheses
2×3 Matrix{Int64}:
 1  1  0
 0  1  1

julia> hc.labels
2-element Vector{String}:
 "a_and_b"
 "b_and_c"
```
