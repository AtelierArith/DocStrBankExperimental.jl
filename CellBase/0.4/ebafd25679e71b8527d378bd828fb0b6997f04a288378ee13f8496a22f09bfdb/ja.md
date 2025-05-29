```
write_res(io::IO, structure::Cell)
```

SHELX形式のデータを、`structure.metadata`に保存されている追加情報を含めて書き出します。

サポートされているキー: `:label`, `:pressure`, `:volume`, `:enthalpy`, `:spin`, `:abs_spin`, `:symm`, `:flag1`, `flag2`, `flag3`。

以下のフィールドも`REM`行として扱われます:

  * `info`: `Dict`が提供されると、キーと値のペアが書き出されます。
  * `comments`: 書き出す追加のコメント。`Vector{<:AbstractString}`として提供する必要があります。

構造の組成は`REM Composition: <E1> <N1> <E2> <N2>`として書き出されます。
