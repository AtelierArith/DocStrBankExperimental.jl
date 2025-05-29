```
@context begin ... end
@context function f() ... end
```

`@context` はローカルコンテキストを作成し、そのコンテキスト内で提供されたコードを実行します。コードが終了すると、コンテキストに登録されたリソースは `ResourceContexts.cleanup!()` によってクリーンアップされます。

コードが `function` 定義である場合、コンテキストブロックは関数本体の周りに挿入されます。
