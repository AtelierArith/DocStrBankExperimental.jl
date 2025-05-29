```
runHF(bs, nuc, nucCoords, config=HFconfig(), N=getCharge(nuc); 
      printInfo=true, infoLevel=2) -> 
HFfinalVars

runHF(bs, nuc, nucCoords, N=getCharge(nuc), config=HFconfig(); 
      printInfo=true, infoLevel=2) -> 
HFfinalVars
```

Quiqboxでハートリー–フォック法を実行するためのメイン関数。返される結果と関連情報は[`HFfinalVars`](@ref)に格納されます。

```
runHFcore(args...; printInfo=false, infoLevel=2) -> 
Tuple{Tuple{Vararg{HFtempVars}}, Bool}
```

`runHF`のコア関数で、`runHF`と同じ位置引数を受け取りますが、反復中に収集されたデータ（`HFtempVars`）とSCF手順が収束したかどうかのブール値を返します。

≡≡≡ 位置引数 ≡≡≡

`bs::Union{     BasisSetData{T, D},      AbstractVector{<:AbstractGTBasisFuncs{T, D}},      Tuple{Vararg{AbstractGTBasisFuncs{T, D}}} } where {T, D}`: ハートリー–フォック近似に使用される基底セット。

`nuc::Union{     Tuple{String, Vararg{String, NNMO}} where NNMO,      AbstractVector{String} }`: 研究対象のシステム内の原子核。

`nucCoords::Union{AbstractArray{NTuple{D, T}, 1}, Tuple{NTuple{D, T}, Vararg{NTuple{D, T}, NNMO}}, AbstractVector{<:AbstractVector{<:T}}, Tuple{TL, Vararg{TL, NNMO}} where TL<:(AbstractVector{<:T})} where {T, D, NNMO}`: 対応する原子核の座標。

`config::HFconfig`: 選択されたハートリー–フォック法の設定。詳細については[`HFconfig`](@ref)を参照してください。

`N::Union{Int, Tuple{Int}, NTuple{2, Int}}`: 電子の総数、または同じスピン構成の電子の数。**注意:** `N::NTuple{2, Int}`は制限なしハートリー–フォック（UHF）のみサポートされています。

≡≡≡ キーワード引数 ≡≡≡

`printInfo::Bool`: 反復ステップと結果の情報を出力するかどうか。

`infoLevel::Int`: `printInfo=true`のときに印刷される情報の詳細レベル。絶対値が高いほど、より多くの中間ステップが印刷されます。`infoLevel`が`5`に達すると、すべてのステップが印刷されます。
