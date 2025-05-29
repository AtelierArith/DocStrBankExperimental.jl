```
freeze(pkg; julia=juliaversion(), relaxed = false, copy_manifest=false)
```

現在のパッケージのバージョンをProject.tomlファイルに追加することで固定します。

# 引数

  * pkg:           モジュールPkg
  * julia:         Juliaの互換性のためのバージョン文字列、例："1"または"~1.8, ~1.9, ~1.10"
  * relaxed:       `true`に設定すると、生成される互換エントリからマイナーバージョン番号が省略されます。これは、非破壊的なマイナーアップデートが許可されることを意味します。
  * copy_manifest: `true`の場合、現在の`Manifest.toml`ファイルのコピーを"Manifest.toml-1.10-windows"のような命名規則を使用して作成します。
  * keep:          `true`の場合（デフォルト）、既存の互換エントリはそのまま保持されます（順序が変更される場合があります）。

厳密な互換性のためには、プロジェクトでテストしたJuliaのバージョンのみを追加してください。

# 例

```julia-repl
using Pkg, PkgHelpers
freeze(Pkg, copy_manifest=true)
freeze(Pkg; julia="~1.9, ~1.10", copy_manifest=true)
```
