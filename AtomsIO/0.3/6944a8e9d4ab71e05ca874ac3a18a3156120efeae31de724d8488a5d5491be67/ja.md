```
save_system([parser], file::AbstractString, system::AbstractSystem; kwargs...)
```

AtomsBase互換のシステムを`file`に保存します。デフォルトでは、`AtomsIO`は指定されたファイル形式に対して適切なパーサーを自動的に選択します。特定のパーサー（例えば、[`AtomsIO.ExtxyzParser`](@ref)や[`AtomsIO.ChemfilesParser`](@ref)）を強制するには、最初の引数として使用します。一部のパーサーは追加のキーワード引数をサポートしています。例えば、`AseParser`はASE内部の入力/出力形式の選択を上書きするための`format`引数をサポートしています。
