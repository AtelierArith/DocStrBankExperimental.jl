```
explicit_imports_nonrecursive(mod::Module, file=pathof(mod); skip=(mod, Base, Core), strict=true)
```

[`explicit_imports`](@ref)の非再帰バージョンであり、モジュール`mod`自体のみを分析し、そのサブモジュールは分析しません。詳細についてはその関数を参照してください。

## キーワード引数

  * `skip=(mod, Base, Core)`: リストされたモジュール（またはそのサブモジュール）から来る名前はスキップされます。デフォルトで`mod`が含まれているため、サブモジュールからエクスポートされた名前の暗黙的なインポートはデフォルトではカウントされません。
  * `strict=true`: `strict=true`の場合、分析が正確に実行できなかった場合（例えば、動的な`include`文のため）、結果は`nothing`になります。`strict=false`の場合、すべてのケースで結果が返されますが、正確でない可能性があります。
