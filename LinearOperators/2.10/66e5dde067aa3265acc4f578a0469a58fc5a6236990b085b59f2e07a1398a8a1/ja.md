```
Z = opRestriction(I, ncol)
Z = opRestriction(:, ncol)
```

`ncol`サイズのベクトルをインデックス`I`に制限するLinearOperatorを作成します。操作`Z * v`は`v[I]`に相当します。`I`は`:`であることもできます。

```
Z = opRestriction(k, ncol)
```

`opRestriction([k], ncol)`のエイリアスです。
