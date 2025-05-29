```
box(cornerpoint1, cornerpoint2; action=:none, vertices=false, reversepath=false)
box(cornerpoint1, cornerpoint2, action; vertices=false, reversepath=false)
```

2つの点の間にボックス（長方形）を作成し、現在のパスに追加します。その後、`action`を適用します。

`vertices=true`を使用すると、アクションを実行するのではなく、4つのコーナーポイント（左下、左上、右上、右下）の配列を返します。

`reversepath`はパスの方向を逆にし（ポイントを左下、右下、右上、左上の順に返します）。
