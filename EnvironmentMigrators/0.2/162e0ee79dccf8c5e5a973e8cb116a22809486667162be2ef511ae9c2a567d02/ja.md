```
migrate(m::AbstractEnvironmentMigrator; backup = true, update = true)
```

環境を別の場所に移動します。 `backup` - 対象環境のバックアップを行うかどうか（`true`）または行わないか（`false`）。 `update` - ソース環境の更新を行うかどうか（`true`）または行わないか（`false`）。

# 拡張ヘルプ

典型的な移行手順は次のとおりです。

1. 指定されている場合は、ファイルを移動して対象環境のバックアップを取ります。
2. ソースから対象環境に（Julia）Project.tomlをコピーします。
3. ソースから対象環境に（Julia）Manifest.tomlをコピーします。
4. 対象環境をアクティブにします。
5. `Pkg.status()`
6. `Pkg.upgrade_manifest()` - エラーが発生した場合はスキップ
7. `Pkg.resolve()`
8. `Pkg.instantiate()`
9. `Pkg.status()`
10. `Pkg.update()`
