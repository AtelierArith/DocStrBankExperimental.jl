```
hold(flag::Bool)
```

複数のプロットを組み合わせるためのホールドフラグを設定します。

`hold(true)`は以前のプロットをクリアするのを防ぎ、`hold(false)`が呼ばれるまで次のプロットが前のプロットの上に描画されます。

プロット関数でキーワード引数`hold=<true/false>`を使用して、プロットの作成中にホールドフラグを設定します。
