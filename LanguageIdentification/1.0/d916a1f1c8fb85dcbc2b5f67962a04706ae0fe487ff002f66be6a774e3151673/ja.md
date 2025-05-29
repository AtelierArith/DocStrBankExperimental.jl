```
langid(text, languages::Vector{String}, profiles::Vector{Dict{Vector{UInt8}, Float32}}; ngram=NGRAM)
```

与えられたテキストの言語を、提供された言語プロファイルに基づいて返します。

# 引数

  * `text`: 言語識別のために分析される文字列または文字列のコレクション。
  * `languages::Vector{String}`: 選択可能な言語のリスト。この引数を省略すると、すべてのサポートされている言語が使用されます。
  * `profiles::Vector{Dict{Vector{UInt8}, Float32}}`: 同定に使用する言語プロファイル。この引数を省略すると、デフォルトのプロファイルが使用されます。
  * `ngram::Union{Int, AbstractVector}`: 言語検出に使用するutf-8バイトn-グラムの長さ。デフォルト値は[`initialize`](@ref)で設定された値であり、その値を超えてはいけません。

# 戻り値

  * 与えられたテキストの言語。
