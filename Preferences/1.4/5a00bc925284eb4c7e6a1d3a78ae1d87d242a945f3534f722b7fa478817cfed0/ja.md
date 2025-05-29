```
set_preferences!(uuid_or_module_or_name, prefs::Pair{String,Any}...;
                 export_prefs=false, active_project_only=true, force=false)
```

指定された uuid::UUID/module::Module/name::String に対して一連の設定を行います。これは、`prefs` として渡されたペアによって識別されます。設定は、ロードパス上の `Project.toml` および `LocalPreferences.toml` ファイルから読み込まれ、値が統合されて一貫したビューが作成されます。設定は `LOAD_PATH` の順序で優先され、パッケージの解決と同様です。`Project.toml` ファイルに保存された設定は「エクスポートされた」と見なされ、パッケージのインストール間で簡単に共有されますが、`LocalPreferences.toml` ファイルは通常共有されないローカル設定を表すことを意図しています。`LocalPreferences.toml` の設定は、適切な場合に `Project.toml` の設定を上書きします。

`set_preferences!(uuid, "key" => value)` を実行した後、将来の `load_preference(uuid, "key")` の呼び出しは一般的に `value` を返しますが、これは `load_path()` の上位要素からの設定の継承によるマージの例外があります。この継承を制御するために、`set_preferences!()` に渡すことができる特別な値が2つあります：`nothing` と `missing`。

  * `missing` を値として渡すと、関連するキーのすべてのマッピングが現在の `LocalPreferences.toml` 設定のレベルから削除され、設定のチェーンの上位に設定された設定が通過できるようになります。この値は、設定をクリアしたいが、このキーの上位の設定を継承したい場合に使用します。
  * `nothing` を値として渡すと、関連するキーのすべてのマッピングが現在の `LocalPreferences.toml` 設定のレベルから削除され、設定のチェーンの上位に設定された設定が通過するのをブロックします。内部的には、これにより、`LocalPreferences.toml` ファイルの `__clear__` リストに設定キーが追加され、上位の環境からの設定が漏れ出すのを防ぎます。

`missing` と `nothing` の動作は似ている（どちらも現在の設定をクリアする）一方で、正反対です（1つは設定の継承を許可し、もう1つは許可しない）。これらは通常の `set_preferences!()` 呼び出しと組み合わせることもできます：

```julia
@set_preferences!("compiler_options" => nothing)
@set_preferences!("compiler_options" => Dict("CXXFLAGS" => "-g", LDFLAGS => "-ljulia"))
```

上記のスニペットは、最初に `"compiler_options"` キーの継承の影響をクリアし、その後に設定オプションを設定します。これにより、将来その設定を読み込むと、ここで保存されたものと正確に一致します。もし、設定のチェーンの上位からの継承を再度有効にしたい場合は、最初に `missing` を渡すことで同じことができます。

`export_prefs` オプションは、設定される設定が `LocalPreferences.toml` または `Project.toml` に保存されるべきかどうかを決定します。

`active_project_only` フラグは、設定が現在アクティブなプロジェクト内に設定されることを保証します（`Base.active_project()` によって決定されます）。ターゲットパッケージが依存関係としてリストされていない場合は、`extras` セクションの下に追加されます。このフラグが設定されていない場合、ターゲットパッケージがアクティブなプロジェクトに見つからないと、`set_preferences!()` はそのモジュールを含む環境をロードパス上で検索し、最初に見つけたものに設定を行います。見つからない場合は、アクティブなプロジェクトに設定を行い、追加の依存関係として追加します。
