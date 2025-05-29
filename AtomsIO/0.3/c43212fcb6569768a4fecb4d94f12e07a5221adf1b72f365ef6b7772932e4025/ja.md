```
load_trajectory([parser], file::AbstractString; kwargs...)
```

`file` から軌道を読み込み、`AtomsBase` 互換の構造体のベクターを返します。`parser` を提供すると、自動的な `AtomsIO` の選択が上書きされます。
