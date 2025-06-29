```
project(R::AbstractLazyReachSet, variables::NTuple{D,Int};
        check_vars::Bool=true) where {D}
```

与えられた変数によって張られた部分空間にリーチセットを射影します。

### 入力

  * `R`          – リーチセット
  * `vars`       – 射影のための変数のタプル
  * `check_vars` – （オプション、デフォルト: `true`）`true`の場合、与えられた変数インデックス `vars` が `R` の変数の部分集合であることを確認します

### 出力

`vars` によって与えられる変数インデックスを持つ `SparseReachSet`。

新しいリーチセットの型は、リーチセット `R` の型に依存します：

  * `R` がハイパーレクタングルセットを含む場合、出力はハイパーレクタングルです。
  * `R` がゾノトピックセットを含む場合、出力はゾノトープです。
  * それ以外の場合、返される型はポリトープであり、制約表現または頂点表現のいずれかになります。これは次第に次元と `M` の特性に依存します。詳細については `LazySets.project` を参照してください。

### 注意事項

この関数は、リーチセットを低次元の部分空間に射影するために使用できます。射影は具体的であり、リーチセット `X = set(R)` を与えられた変数 `vars` に関連付けられた射影行列 `M` を通じて新しいリーチセットにマッピングすることから成ります。

時間変数に射影するには、インデックス `0` を使用します。たとえば、`(0, 1)` は時間変数と `R` の最初の変数に射影します。
