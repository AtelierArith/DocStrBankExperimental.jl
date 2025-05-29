```
Readme(;
    file="~/.julia/packages/PkgTemplates/MepaC/templates/README.md",
    destination="README.md",
    inline_badges=false,
)
```

他の含まれているプラグインのバッジを含む `README` ファイルを作成します。

## キーワード引数

  * `file::AbstractString`: `README` のテンプレートファイル。
  * `destination::AbstractString`: リポジトリのルートに対するファイルの宛先。例えば、`"README"` や `"README.rst"` の値が望ましいかもしれません。
  * `inline_badges::Bool`: バッジをパッケージ名と同じ行に置くかどうか。
  * `badge_order::Vector{typeof(Plugin)}`: バッジが表示される順序のプラグイン。
  * `badge_off::Vector{typeof(Plugin)}`: バッジを追加しないプラグイン。
