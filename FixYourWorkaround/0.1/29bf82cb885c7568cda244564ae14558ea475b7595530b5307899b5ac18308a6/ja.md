```
package_compatible(package_name::String, version::String)
```

package_name@versionがProject.tomlの互換セクションにおいて範囲内であるかを確認します。

# 引数

  * `package_name::String`: パッケージの名前
  * `version::String`: 範囲内であるか確認するパッケージのバージョン

# キーワード

  * `toml_path::String`: Project.tomlファイルへのパス

# 戻り値

  * `Bool`: バージョンが互換バージョン内であるかどうか

# 例外

  * `PackageNotInCompat`: package_nameが互換セクションに見つかりませんでした
  * `CompatNotFound`: Project.tomlに互換セクションが見つかりませんでした
  * `VersionOutsideSpec`: バージョンがもはや互換バージョンの範囲内ではありません
