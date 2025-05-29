```
aggregate_attractor_fractions(
    fractions_cont, attractors_cont, featurizer, group_config [, info_extraction]
)
```

類似のアトラクタの吸引盆の割合の推定曲線を、[`GroupingConfig`](@ref)で使用されるのと同じパイプラインを使用して集約します。この関数の最も一般的な用途は、[`global_continuation`](@ref)の出力を[`RecurrencesFindAndMatch`](@ref)で変換し、パラメータ空間を超えても類似のアトラクタを1つの「アトラクタ」にグループ化することです。したがって、それらの吸引盆の割合が集約されます。

この関数は、[`basins_fractions`](@ref)の出力を使用して、単一のパラメータ構成内でアトラクタとその割合を集約するためにも使用できます。

この関数は、[`AttractorsViaRecurrences`](@ref)の精度とパフォーマンスが必要な場合に便利ですが、プレゼンテーションや分析の目的で[`AttractorsViaFeaturizing`](@ref)のように類似のアトラクタを「グループ化」する便利さも求める場合に役立ちます。たとえば、多種間の競争ダイナミクスの高次元モデルは、極端な多安定性を持つ可能性があります。この多安定性を見つけた後、特定の種が絶滅しているかどうかの2つのグループにすべてのアトラクタを集約することに関心があるかもしれません。これは、[多安定競争モデルにおける種の絶滅](@ref)で強調されている例です。

## 入力

1. `fractions_cont`: ラベルを吸引盆の割合にマッピングする辞書のベクター。
2. `attractors_cont`: ラベルをアトラクタにマッピングする辞書のベクター。1番目と2番目の引数は、[`global_continuation`](@ref)の[`RecurrencesFindAndMatch`](@ref)の戻り値と正確に同じです（または、[`basins_fractions`](@ref)の戻り値であることもできます）。
3. `featurizer`: アトラクタを後でグループ化するための適切な特徴にマッピングする1引数関数。[`GroupingConfig`](@ref)によって期待される特徴は`SVector`です。
4. `group_config`: [`GroupingConfig`](@ref)のサブタイプ。
5. `info_extraction`: 特徴のベクターを受け取り、特徴の説明を返す関数。すなわち、[`FeaturizeGroupAcrossParameter`](@ref)と正確に同じです。5番目の引数はオプションで、特徴の重心がデフォルトです。

## 戻り値

1. `aggregated_fractions`: `fractions_cont`と同じですが、今は集約されたアトラクタの割合が含まれています。
2. `aggregated_info`: `aggregated_fractions`の新しいラベルを`info_extraction`を使用して抽出された情報にマッピングする辞書。

## アトラクタを直接クラスタリングする

*(これはかなり高度です)*

ここで、状態空間距離（[`set_distance`](@ref)）に基づいてアトラクタをグループ化するためにDBSCANクラスタリングアプローチを使用することもできます。これには、DBSCAN実装で期待される距離行列を作成します。そのためには、`featurizer`として`identity`を使用し、`clust_distance_metric = set_distance`で[`GroupViaClustering`](@ref)を`group_config`として選択し、[`GroupViaClustering`](@ref)を初期化する際に`optimal_radius_method`に数値値を提供し、さらに`info_extraction`引数には、*`StateSpaceSet`のベクター*を期待し、記述子を出力する関数を提供する必要があります。たとえば、`info_extraction = vector -> mean(mean(x) for x in vector)`のようになります。 ```
