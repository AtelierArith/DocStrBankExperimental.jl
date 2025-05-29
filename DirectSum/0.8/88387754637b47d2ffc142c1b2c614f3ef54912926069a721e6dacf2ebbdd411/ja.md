```
@mixedbasis
```

`Submanifold` 要素を生成し、`Manifold` は `V⊕V'` で指定されます。このマクロの結果として、生成されたすべての `Submanifold{V⊕V',G}` 要素が、指定された名前でローカルワークスペースで利用可能になります。最初の引数は擬似スカラーの仕様を提供し、2 番目の引数は `Manifold` の変数名、3 番目と 4 番目の引数は `Submanifold` ベクトル名（および共ベクトル基底名）の変数プレフィックスです。`@mixedbasis M` のデフォルトは `@mixedbasis M V v w ∂ ϵ` です。
