```
mutate!(
    tree::N,
    member::P,
    ::Val{S},
    mutation_weights::AbstractMutationWeights,
    options::AbstractOptions;
    kws...,
) where {N<:AbstractExpression,P<:PopMember,S}
```

与えられた `tree` と `member` に対して、指定された突然変異タイプ `S` を使用して突然変異を実行します。さまざまな `kws` が提供されており、いくつかの突然変異に必要な他のデータにアクセスできます。

この関数をオーバーロードして、新しい `AbstractMutationWeights` タイプの新しい突然変異タイプを処理することができます。

# キーワード

  * `temperature`: アニーリングベースの突然変異のための温度パラメータ。
  * `dataset::Dataset`: スコアリングに使用されるデータセット。
  * `cost`: 突然変異前のメンバーのコスト。
  * `loss`: 突然変異前のメンバーの損失。
  * `curmaxsize`: 現在の最大サイズ制約。これは `options.maxsize` とは異なる場合があります。
  * `nfeatures`: データセット内の特徴の数。
  * `parent_ref`: 突然変異したメンバーの親への参照（ログ記録目的のみ使用）。
  * `recorder::RecordType`: 突然変異の詳細を記録するためのレコーダー。

# 戻り値

突然変異した木またはメンバー（ただし両方ではない）、実行された評価の数（あれば）、および突然変異関数から即座に戻るか、`next_generation` 関数が突然変異を受け入れるか拒否するかを処理するかどうかを含む `MutationResult{N,P}` オブジェクト。たとえば、`simplify` 操作は損失を変更しないため、常に即座に戻ることができます。
