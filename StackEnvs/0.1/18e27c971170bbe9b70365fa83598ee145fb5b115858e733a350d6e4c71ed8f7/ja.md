```
ensure_in_stack(env::StackEnv)::StackEnv
```

共有環境 `env.name` が `env.packages` とともにスタックにあることを確認します。

環境スタックは `Base.LOAD_PATH` です。

もし `env.name` が共有環境を指していない場合は、それを作成し `env.packages` を追加します。さらに、`env.name` がスタックにない場合は、スタックに追加します。

この処理が完了した後、パッケージ `env.packages` はアクティブなプロジェクトで利用可能であるべきです。

`ensure_in_stack` は `env.packages` を環境の `Project.toml` にあるパッケージのリストと比較し、環境が最初に作成されて以来追加したかもしれない不足しているパッケージを追加します。

サポートされていないこと:

  * 何らかの理由で環境からパッケージを削除すること。
  * バージョン、UUID などを指定または確認すること。

関数 [`update_env`](@ref) は、`env.packages` にあるすべてのパッケージを環境に無条件に追加し、アップグレードを行う可能性があります（私は確信がありません）。

[`StackEnv`](@ref) を参照してください。
