```
box(points::Array; action=:none,
    reversepath=reversepath,
    vertices=vertices)
box(points::Array; action=:none,
    reversepath=reversepath,
    vertices=vertices)
```

配列の最初の2つのポイントを使用してボックス/長方形を作成し、対角のコーナーを定義し、それを現在のパスに追加します。次に、`action`を適用します。

`vertices=true`を使用すると、アクションを実行するのではなく、4つのコーナーポイントの配列（左下、左上、右上、右下）を返します。
