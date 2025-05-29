```
load_system([parser], file::AbstractString; kwargs...)
load_system([parser], file::AbstractString, index; kwargs...)
```

`file`からAtomsBase互換のシステムを読み込みます。`file`に複数の構造が含まれている場合、最後のエントリが返されます。`index`が指定されている場合、構造のリストにインデックスを付けて、それぞれのシステムを返します。

デフォルトでは、`AtomsIO`は指定されたファイル形式に対して適切なパーサーを自動的に選択します。特定のパーサー（例えば、[`AtomsIO.ExtxyzParser`](@ref)や[`AtomsIO.ChemfilesParser`](@ref)）を最初の引数として使用することで強制することができます。一部のパーサーは追加のキーワード引数をサポートしています。例えば、`AseParser`はASE内部の入力/出力形式の選択を上書きするための`format`引数をサポートしています。
