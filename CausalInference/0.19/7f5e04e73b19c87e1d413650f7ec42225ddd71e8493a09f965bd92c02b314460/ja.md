```
alt_test_dsep(g, X, Y, S, veto = no_veto)
```

グラフ `g` において、頂点の集合 `X` と `Y` が集合 `S` を考慮して d-分離されているかどうかを確認します。

内部で gensearch を使用する `test_dsep` 関数の代替手段です。少し遅くなる可能性があります。
