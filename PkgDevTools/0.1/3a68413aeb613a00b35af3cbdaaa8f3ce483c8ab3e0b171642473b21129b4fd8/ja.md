```
synchronize_compats(code_dir::AbstractString)
```

この関数は

  * `code_dir`内のすべてのProject.tomlファイルを再帰的に見つけます
  * コンパチビリティエントリを収集します
  * 一貫性のないコンパチビリティエントリを見つけます
  * ユーザーにどのバージョン（ある場合）に更新するかを尋ね、Project.tomlファイルをそれに応じて修正します。
