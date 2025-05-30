```
read_workspace(path_to_workspace_file::String)
```

UMCU Raw Export Toolパッチを使用してエクスポートされたJSONファイルからワークスペースを読み込みます。

# 引数

  * `path_to_workspace_file::String`: ワークスペースファイルへのパス。関数はパスからファイル拡張子を削除し、`.json`を追加します。

# 戻り値

  * `workspace`: ファイルから読み込まれたワークスペースを表す`Workspace`オブジェクト。ワークスペース内のすべての整数は、それに対応する列挙値に置き換えられます。

# 例

```
workspace = read_workspace("/path/to/workspace")
```
