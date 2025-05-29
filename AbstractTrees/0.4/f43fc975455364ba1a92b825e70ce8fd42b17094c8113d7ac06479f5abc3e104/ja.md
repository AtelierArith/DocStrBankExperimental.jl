```
isroot(x)
```

`x`が木の絶対ルートであるかどうか。より具体的には、`parent(x) ≡ nothing`、または`parent(root, x) ≡ nothing`の場合に`true`を返します。つまり、任意のノードはある木のルートですが、この関数は`AbstractTrees`インターフェースを使用して取得できない親を持つノードに対してのみ`true`を返します。
