```
print_explicit_imports([io::IO=stdout,] mod::Module, file=pathof(mod); skip=(mod, Base, Core),
                       warn_implicit_imports=true,
                       warn_improper_explicit_imports=true,
                       warn_improper_qualified_accesses=true,
                       report_non_public=VERSION >= v"1.11-",
                        strict=true)
```

[`explicit_imports`](@ref) を実行し、[`improper_explicit_imports`](@ref) および [`improper_qualified_accesses`](@ref) の結果とともに出力します。

特定の印刷は、将来の非破壊的リリースの ExplicitImports で変更される可能性があることに注意してください。

## キーワード引数

  * `skip=(mod, Base, Core)`: リストされたモジュール（またはそのサブモジュール）からの名前はスキップされます。デフォルトで `mod` が含まれているため、そのサブモジュールからエクスポートされた名前の暗黙的インポートはデフォルトでカウントされません。
  * `warn_improper_explicit_imports=true`: 設定されている場合、この関数は他のモジュールからの「不適切な」インポートに関する情報も出力します。
  * `warn_improper_qualified_accesses=true`: 設定されている場合、この関数は他のモジュールからの「不適切な」資格付きアクセスに関する情報も出力します。
  * `strict=true`: `strict` が設定されている場合、分析が正確に実行できなかった場合（例えば、動的な `include` ステートメントのため）に、モジュールは分析不可能として記録されます。`strict=false` の場合、すべてのケースで結果が返されますが、不正確な場合があります。
  * `show_locations=false`: 名前が使用されている場所を印刷するかどうか。
  * `separate_lines=false`: 各 `using` ステートメントを別の行に印刷するかどうか。`show_locations=true` の場合は自動的に発生します。
  * `linewidth=80`: この長さまでの行にフォーマットします。1行に1つの名前を印刷するには0に設定します。
  * `report_non_public=VERSION >= v"1.11-"`: 非公開の名前（エクスポートされていないか、公開としてマークされていない名前）へのアクセスやインポートがある場合に報告します。デフォルトでは、Julia v1.11+ のみで有効になります。
  * `allow_internal_accesses=true`: false の場合、同じパッケージ内の他のモジュールへの非所有または非公開の資格付きアクセスを報告します。
  * `allow_internal_imports=true`: false の場合、同じパッケージ内の他のモジュールからの非所有または非公開の明示的インポートを報告します。

[`check_no_implicit_imports`](@ref)、[`check_no_stale_explicit_imports`](@ref)、[`check_all_qualified_accesses_via_owners`](@ref)、および [`check_all_explicit_imports_via_owners`](@ref) も参照してください。
