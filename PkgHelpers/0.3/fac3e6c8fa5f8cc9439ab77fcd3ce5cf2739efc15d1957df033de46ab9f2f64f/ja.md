```
lower_bound(pkg; julia=nothing, relaxed = false, copy_manifest=false)
```

現在のパッケージバージョンをProject.tomlファイルの互換性セクションに下限として追加します。

# 引数

  * pkg:           モジュールPkg
  * julia:         Juliaの互換性のためのバージョン文字列、例："1"または"1.8"
  * relaxed:       `true`に設定すると、生成される互換性エントリからマイナーバージョン番号が省略されます。
  * copy_manifest: `true`の場合、現在の`Manifest.toml`ファイルのコピーを作成し、"Manifest.toml-1.10-windows"のような命名規則を使用します。
  * keep:          `true`の場合（デフォルト）、既存の互換性エントリはそのまま保持されます（順序が変更される場合があります）。

# 例

```julia-repl
using Pkg
lower_bound(Pkg)
```
