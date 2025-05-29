```
@dualbasis
```

`V'`で指定された`Manifold`を持つ`Submanifold`要素を生成します。このマクロの結果として、その`TensorBundle`によって生成されたすべての`Submanifold{V',G}`要素が、指定された名前でローカルワークスペースで利用可能になります。最初の引数は擬似スカラーの仕様を提供し、2番目の引数は双対`Manifold`の変数名、3番目と4番目の引数は`Submanifold`共変ベクトル名（およびテンソル場基底名）の変数プレフィックスです。`@dualbasis M`のデフォルトは`@dualbasis M VV w ϵ`です。
