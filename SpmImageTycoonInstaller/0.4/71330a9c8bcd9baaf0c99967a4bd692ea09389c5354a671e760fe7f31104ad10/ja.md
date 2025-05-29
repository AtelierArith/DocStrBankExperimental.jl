```
install(dir::String=""; ver::String="main", shortcuts_only::Bool=false,
    interactive::Bool=true, debug::Bool=false, test::Bool=false)::Nothing
```

SpmImageTycoonをインストールします。

特定のディレクトリを`dir`として直接指定できます。

`ver`はインストールするバージョンを指定します：`"main"`（デフォルト）、`"dev"`は開発バージョン、`"local"`はローカルにインストールされた`SpmImageTycoon`のバージョンです。

`shortcuts_only`が`true`の場合、アプリ自体ではなくショートカットのみがインストールされます（アプリを以前にインストールした場合のみ使用してください - そうでないとショートカットは機能しません）。`interactive`が`false`の場合、インストールはユーザーの操作なしで進行します。`debug`が`true`の場合、インストールの裏側の出力が表示されます（ログファイルに書き込まれるのではなく）。`test`が`true`の場合、インストールはシミュレーションのみ行われ、コンパイルはスキップされます。
