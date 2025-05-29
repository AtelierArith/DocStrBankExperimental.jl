```julia
symeigs_analysis(
    symeigsv::AbstractVector{<:AbstractVector{<:AbstractVector{<:Number}}},
    brs::Crystalline.Collection{Crystalline.NewBandRep{D}};
    ...
) -> Array{Crystalline.SymmetryVector{_A}, 1} where _A
symeigs_analysis(
    symeigsv::AbstractVector{<:AbstractVector{<:AbstractVector{<:Number}}},
    brs::Crystalline.Collection{Crystalline.NewBandRep{D}},
    F::Crystalline.SmithNormalForm.Smith{var"#s22", Q, V} where {var"#s22"<:Integer, Q<:AbstractMatrix{var"#s22"}, V<:AbstractVector{var"#s22"}};
    kws...
) -> Array{Crystalline.SymmetryVector{_A}, 1} where _A

```

与えられた対称固有値データのベクトル `symeigsv` と関連するバンド表現のセット `brs` に基づいて、各要素が最小占有数および互換性を尊重したバンドグループであるバンドのセットを `Vector{SymmetryVector{D}}` として返します。最も低いバンドが最初に返されます。

## 入力引数

  * `symeigsv`: 対称固有値の三重入れ子ベクトルで、次のインデックス付け規則に従います。`symeigsv[kidx][bandidx][opidx]` は、`kidx` 番目の **k**-点および `bandidx` 番目のバンドの対称固有値を、`kidx` 番目の **k**-点の小群における `opidx` 番目の対称操作の作用の下で与えます。小群操作のソートは、`group(irreps(brs)[kidx])` のものと一致する必要があります。
  * `brs :: Collection{NewBandRep{D}}`: バンド表現のコレクションで、[`calc_bandreps`](@ref) から得られた一連の `NewBandRep{D}` オブジェクトを反復処理します。`primitivized` 形式で提供されることが期待されています（[`primitivize(::Collection{<:NewBandRep})`](@ref) を参照）。小群の不変表現は、`brs` を介して暗黙的に指定されます（`irreps(brs)` を介して）、対応する小群およびその関連する演算子のソートも同様です（`group.(irreps(brs))` を介して）。`symeigsv` の対称固有値のソートは、`group(irreps(brs)[kidx])[opidx]` が `symeigsv[kidx][:][opidx]` の要素と一致するようにされていると仮定されます。
  * `F::Smith{<:Integer}`: オプション引数で、バンド表現行列 `stack(brs)` のスミス正規形に対応します。関数への繰り返し呼び出しのために、再計算を避けるために明示的に供給できます（`smith` を参照）。

## キーワード引数

キーワード引数 `kws` は、対称固有値 `symeigsv` から不変表現の重複度を決定する [`find_multiplicities`](@ref) に転送されます。

低解像度の計算（すなわち、`symeigsv` にかなりの数値誤差がある場合）では、[`find_multiplicities`](@ref) によって使用される絶対許容誤差 `atol`（デフォルトは 0.02）を増加させることが有益です。
