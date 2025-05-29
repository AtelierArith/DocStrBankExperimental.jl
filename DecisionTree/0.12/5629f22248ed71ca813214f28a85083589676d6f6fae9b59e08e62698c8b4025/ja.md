```
wrap(node::DecisionTree.Node, info = NamedTuple())
wrap(leaf::DecisionTree.Leaf, info = NamedTuple())
```

各 `node`（または `leaf`）に追加情報 `info` を加え、両方を `InfoNode`/`InfoLeaf` でラップします。

通常、`node` または `leaf` は、`DecisionTree.jl` のネイティブインターフェースを使用するか、このパッケージで利用可能な他のインターフェース（`MLJ`、ScikitLearnなど; 詳細はそれらのドキュメントを参照）を介して決定木を作成することで取得されます。ネイティブインターフェースの `build_tree` 関数を使用すると、そのようなオブジェクトが返されます。

この方法で取得した DecisionTree `dc` を、ここで実装された `AbstractTrees` インターフェースによる抽象化レイヤーで使用し、オプションで特徴名 `feature_names` および/またはクラスラベル `class_labels`（どちらも文字列の配列）を追加するには、次の構文を使用します。

1. `wdc = wrap(dc)`
2. `wdc = wrap(dc, (featurenames = feature_names, classlabels = class_labels))`
3. `wdc = wrap(dc, (featurenames = feature_names, ))`
4. `wdc = wrap(dc, (classlabels  = class_labels, ))`

最初のケースでは、`dc` は単にラップされ、情報は追加されません。2番目は特徴名とクラスラベルの両方を追加します。最後の2つのケースでは、いずれかの情報が追加されます（タプルにするために必要な末尾のカンマに注意してください）。
