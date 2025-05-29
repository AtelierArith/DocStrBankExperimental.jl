```
install_shortcuts(dir::String=""; test::Bool=false, interactive::Bool=true)::Nothing
```

SpmImage Tycoonのショートカットをインストールします。アプリを以前にインストールした場合のみ使用してください - そうでないとショートカットは機能しません。

`test`が`true`の場合、インストールはシミュレーションされ、コンパイルはスキップされます。`interactive`が`false`の場合、インストールはユーザーの対話なしで進行します。
