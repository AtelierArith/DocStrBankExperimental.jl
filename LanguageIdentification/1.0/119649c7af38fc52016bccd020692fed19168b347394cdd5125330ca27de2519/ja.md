```
langprob(text, languages::Vector{String}, profiles::Vector{Dict{Vector{UInt8}, Float32}}; topk=5, ngram=NGRAM)
```

与えられたテキストの言語に基づく確率分布を、提供された言語プロファイルに基づいて返します。

# 引数

  * `text`: 言語識別のために分析される文字列または文字列のコレクション。
  * `languages::Vector{String}`: 選択可能な言語のリスト。この引数が提供されない場合、[`supported_languages`](@ref) 関数によって返されるすべての言語が使用されます。
  * `profiles::Vector{Dict{Vector{UInt8}, Float32}}`: 同定に使用する言語プロファイル。この引数が提供されない場合、デフォルトのプロファイルが使用されます。
  * `topk::Int`: 返す候補の数。デフォルト値は5です。
  * `ngram::Union{Int, AbstractVector}`: 言語検出に使用するutf-8バイトn-グラムの長さ。デフォルト値は[`initialize`](@ref)で設定された値であり、その値を超えてはいけません。

# 返り値

  * `topk`の言語とその確率のリスト。
