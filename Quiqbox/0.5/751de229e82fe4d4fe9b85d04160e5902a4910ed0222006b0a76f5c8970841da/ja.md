```
genBFuncsFromText(content::String; 
                  adjustContent::Bool=false, 
                  adjustFunction::Function=sciNotReplace, 
                  excludeFirstNlines::Int=0, excludeLastNlines::Int=0, 
                  center::Union{AbstractArray{T}, 
                                NTuple{D, T}, 
                                NTuple{D, ParamBox{T}}, 
                                SpatialPoint{T, D}, 
                                Missing}=(NaN, NaN, NaN), 
                  unlinkCenter::Bool=false, 
                  normalizeGTO::Union{Bool, Missing}=
                                ifelse(adjustContent, true, missing)) where 
                 {D, T<:AbstractFloat} -> 
Array{<:FloatingGTBasisFuncs, 1}
```

`content` から基底セットを生成します。これは、ガウス形式の基底セット `String` であるか、`genBasisFuncText` の出力です。前者の場合、`adjustContent` を `true` に設定する必要があります。`adjustFunction` は `adjustContent=true` の場合にのみ適用され、デフォルトでは `content` の科学的表記の形式を検出して変換するために使用される `function` です。

`excludeFirstNlines` と `excludeLastNlines` は、意図した場合に `content` の最初または最後の数行を除外するために使用されます。`center` は、`content` からすべての基底関数の中心座標を割り当てるために使用されます。`missing` に設定されている場合、`content` から中心情報を読み取ろうとし、対応する各 `FloatingGTBasisFuncs` に対して中心が見つからない場合は `[NaN, NaN, Nan]` とします。`unlinkCenter = true` の場合、各 `FloatingGTBasisFuncs` の中心は入力 `center` の `Base.deepcopy` です。そうでない場合、同じ基盤データを共有するため、一方の値を変更すると他に影響を与えます。中心座標が `content` に含まれている場合、それは `FloatingGTBasisFuncs` のサブシェル情報のすぐ上にある必要があります。例：

```
"""
X        1.0                          0.0                          0.0                   
S    1   1.0   false
         2.0                            1.0
"""
```

最後に、`normalizeGTO` は生成された `FloatingGTBasisFuncs` のフィールド `.normalizeGTO` を指定します。`missing` に設定されている場合（デフォルト）、各 `FloatingGTBasisFuncs` の正規化設定は `content` に依存するため、異なる基底関数は異なる正規化設定を持つ可能性があります。ただし、`Bool` 値に設定されている場合、生成されたすべての基底関数の `.normalizeGTO` はその値に設定されます。
