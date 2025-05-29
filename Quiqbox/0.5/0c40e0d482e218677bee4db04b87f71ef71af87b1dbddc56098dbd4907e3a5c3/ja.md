```
optimizeParams!(pbs, bs, nuc, nucCoords, 
                config=POconfig(), N=getCharge(nuc); 
                printInfo=true, infoLevel=1) -> 
Vector{Any}

optimizeParams!(pbs, bs, nuc, nucCoords, 
                N=getCharge(nuc), config=POconfig(); 
                printInfo=true, infoLevel=1) -> 
Vector{Any}
```

与えられた基底セットのパラメータを最適化するための主な関数です。関連情報の`Vector`を返します。最初の要素は、収束検出がオンの場合（すなわち、`config.threshold`が`NaN`でない場合）に最適化が収束したかどうかの指標であり、そうでない場合は`missing`に設定されます。返される結果には、`config.method`に応じてさらに要素が追加される場合があります。

=== 位置引数 ===

`pbs::AbstractVector{<:ParamBox{T}}`: 基底セットから抽出された最適化されるパラメータ。パラメータが「微分可能」としてマークされている場合、その入力変数の値が最適化されます。

`bs::AbstractVector{<:GTBasisFuncs{T, D}}`: 最適化される基底セット。

`nuc::Union{     Tuple{String, Vararg{String, NNMO}} where NNMO,      AbstractVector{String} }`: 研究対象のシステム内の原子核。

`nucCoords::Union{AbstractArray{NTuple{D, T}, 1}, Tuple{NTuple{D, T}, Vararg{NTuple{D, T}, NNMO}}, AbstractVector{<:AbstractVector{<:T}}, Tuple{TL, Vararg{TL, NNMO}} where TL<:(AbstractVector{<:T})} where {T, D, NNMO}`: 対応する原子核の座標。

`config::POconfig`: 選択されたパラメータ最適化手法の設定。詳細については[`POconfig`](@ref)を参照してください。

`N::Union{Int, Tuple{Int}, NTuple{2, Int}}`: 電子の総数、または同じスピン構成の電子の数。

=== キーワード引数 ===

`printInfo::Bool`: 反復ステップの情報を出力するかどうか。

`infoLevel::Int`: `printInfo=true`のときに印刷される情報の詳細レベル。絶対値が高いほど、より多くの中間ステップやその他の情報が印刷されます。`infoLevel`が`5`に達すると、すべてのステップと利用可能なすべての情報が印刷されます。
