```
struct Alphabet{A,I}
    characters::Vector{A}
    char_to_index::Dict{A, I}
    index_to_char::Dict{I, A}
    default_char = nothing
    default_index
end
```

生物学的シンボルの型 `A` から整数の型 `I` へのマッピングを可能にする構造体です。典型的な使用例は `Alphabet{Char, Int}` です。`Alphabet` は以下の方法で構築できます。

  * シンボルの `Vector` とオプションの型 `I` から、*例* `Alphabet(['A','C','G','T'], UInt8)::Alphabet{Char, UInt8}`
  * `String` とオプションの型から、*例* `Alphabet("ACGT")`
  * マッピング `Dict{A, I}` から、ここで `I<:Integer`: `Alphabet(Dict('A'=>1, 'C'=>2))`
  * デフォルトのアルファベットを使用して `Symbol` から、*例* `Alphabet(:nt)`
  * デフォルトのアルファベットを使用して整数から（`?default_alphabets` を参照）。
