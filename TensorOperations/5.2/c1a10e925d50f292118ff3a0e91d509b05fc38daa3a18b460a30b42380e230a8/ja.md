```
@butensor tensor_expr
```

Bumper.jlを使用して、一時的なテンソルの割り当てを処理します。このマクロはデフォルトのバッファを使用し、テンソル式が評価された後に自動的にリセットされます。このマクロは、すべての一時的な割り当てがBumper.jlによって処理される`@no_escape @tensor tensor_expr`と同等です。

!!! note
    このマクロはBumper.jlがインストールされ、ロードされている必要があります。これは、マクロを使用する前に`using Bumper`または`import Bumper`を実行することで達成できます。

