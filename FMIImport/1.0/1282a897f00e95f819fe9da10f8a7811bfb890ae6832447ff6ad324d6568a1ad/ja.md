```
loadFMU(pathToFMU; unpackPath, cleanup, type)
```

FMUを読み込みます。使用されるFMIバージョンに依存せず（アーカイブの展開中にバージョンがチェックされます）。

# 引数

  * `path::String` FMUファイルを指すパス。

# キーワード

  * `unpackPath::Union{String, Nothing}=nothing` オプションの展開パス。`nothing`の場合、OSに依存した一時ディレクトリが選択されます。
  * `cleanup::Bool=true` 一時ディレクトリを自動的にクリーンアップするかどうかを示すブール値。
  * `type::Union{Symbol, Nothing}=nothing` 利用可能な複数のタイプがある場合のFMUのタイプ（:CS, :ME, :SE）。`nothing`の場合、利用可能なタイプの中から自動的に選択され、優先順位はCS > ME > SEです。
