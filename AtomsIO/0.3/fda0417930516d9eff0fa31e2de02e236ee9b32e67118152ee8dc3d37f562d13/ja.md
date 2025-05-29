```
save_trajectory([parser], file::AbstractString, systems::AbstractVector; kwargs...)
```

`AtomsBase`互換のシステムのリストとして与えられた軌道を`file`に保存します。`parser`を提供すると、自動的な`AtomsIO`の選択が上書きされます。
