GroupingConfig

特徴をグループ化する方法に関する設定構造体のスーパタイプ。[`AttractorsViaFeaturizing`](@ref)や[`aggregate_attractor_fractions`](@ref)など、いくつかの場面で使用されます。

現在利用可能なグループ化設定は次のとおりです：

  * [`GroupViaClustering`](@ref)
  * [`GroupViaNearestFeature`](@ref)
  * [`GroupViaHistogram`](@ref)
  * [`GroupViaPairwiseComparison`](@ref)

## 開発者向け

`GroupingConfig`は拡張可能なインターフェースを定義します。新しいグループ化設定に必要なことは次のとおりです：

1. 新しい型を作成し、`GroupingConfig`をサブタイプとして定義します。
2. グループ化が個々の特徴をグループインデックスにマッピングできる場合は、代わりに**内部関数**`feature_to_group(feature, config)`を拡張します。これにより、[`AttractorsViaFeaturizing`](@ref)を使用して`id = mapper(u0)`を実行することも可能になります。
3. そうでない場合は、関数`group_features(features, config)`を拡張します。パフォーマンス上の利点がある場合は、(2.)が満たされていても`group_features`を拡張することができます。
4. 新しいグループ化ファイルを`grouping/all_grouping_configs.jl`に含め、このドキュメンテーション文字列にリストします。
