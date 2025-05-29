```
SandboxExecutor
```

これは、このパッケージ内のすべての実行バックエンドの基本タイプを表します。有効な具体的サブタイプは、少なくとも以下のメソッドを実装する必要があります。

  * `T()`: すべてのデフォルトで実行エンジンを準備する引数なしのコンストラクタ。
  * `executor_available(::DataType{T})`: 実行者タイプ `T` がこのシステムで利用可能かどうかをチェックします。たとえば、`UserNamespacesExecutor` はLinuxでのみ利用可能であり、さらに特定のカーネルでのみ利用可能です。利用可能性チェックは、その実行者が実際に利用可能かどうかを判断するためにプログラムを実行する場合があります。
  * `build_executor_command(exe::T, config::SandboxConfig, cmd::Cmd)`: 実行時にユーザーの希望するコマンドを指定されたサンドボックス内で実行する `Cmd` オブジェクトを構築します。`config` オブジェクトには、シャードマッピング、環境変数、`stdin`/`stdout`/`stderr` のリダイレクションなど、必要なすべてのメタデータが含まれています...
  * `cleanup(exe::T)`: この実行者が実行中に蓄積した可能性のある永続データストレージをクリーンアップします。

手動で実行者を構築およびクリーンアップすることはできますが、ユーザーは代わりに `with_executor()` の便利関数を使用することをお勧めします：

```
with_executor(UnprivilegedUserNamespacesExecutor) do exe
    run(exe, config, ...)
end
```
