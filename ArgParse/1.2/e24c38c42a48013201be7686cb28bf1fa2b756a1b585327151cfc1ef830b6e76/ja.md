```
import_settings!(settings, other_settings [,args_only])
```

`other_settings`を`settings`にインポートします。両方は[`ArgParseSettings`](@ref)オブジェクトです。`args_only`が`true`の場合（これがデフォルト）、引数テーブルのみがインポートされます。それ以外の場合、デフォルトの引数グループもインポートされ、`prog`、`description`、`epilog`、`usage`、`version`を除くすべての一般設定がインポートされます。

コマンドに関連するサブ設定も再帰的にインポートされます。`args_only`設定はそれらにも適用されます。共通のコマンドがある場合、そのサブ設定はマージされます。

インポート中に競合が発生する可能性があります。`settings.error_on_conflict`が`true`の場合、これはエラーになります。それ以外の場合、競合は`other_settings`を優先して解決されます（競合の処理方法についての詳細な議論は[Conflicts and overrides](@ref)セクションを参照してください）。

引数グループもインポートされます。`settings`と`other_settings`の2つのグループが一致する場合、それらはマージされます（グループは名前で一致するか、名前がない場合は説明で一致します）。

インポートは即座に効果を持つことに注意してください。その後の`other_settings`の変更は`settings`に影響を与えません。

この関数はいつでも使用できます。
