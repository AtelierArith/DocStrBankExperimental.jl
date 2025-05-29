```
print_explicit_imports_script([io::IO=stdout,] path; skip=(Base, Core), warn_improper_explicit_imports=true)
```

`path`にあるスクリプトを分析し、暗黙のエクスポートへの依存関係や「不適切な」明示的インポートに関する情報を出力します（`warn_improper_explicit_imports=true`の場合）。

特定の出力は、将来の非破壊的リリースのExplicitImportsで変更される可能性があることに注意してください。

!!! warning
    この関数が信頼できる結果を提供するためには、スクリプト（または少なくともスクリプト内のすべてのインポート）を実行する必要があります。これは、`Main`に存在する名前を調査することに依存しているためです。


## キーワード引数

  * `skip=(mod, Base, Core)`: リストされたモジュール（またはそのサブモジュール）からの名前はスキップされます。`mod`はデフォルトで含まれているため、そのサブモジュールからエクスポートされた名前の暗黙のインポートはデフォルトではカウントされません。
