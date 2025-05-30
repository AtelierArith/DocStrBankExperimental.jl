```julia
mutable struct TokenStream
```

TokenStreamは、ファイルからトークン化されたデータを読み取ることを可能にし、ファイルの内容をメモリに保持しません。

  * `input::IOStream`: 入力ストリーム
  * `tokens::Vector{SubString{String}}`: メモリに保持されている現在のトークンの配列。
  * `itoken::Int64`: トークン配列内の実際のトークンの位置
  * `lineno::Int64`: IOStream内の行番号
  * `comment::Char`: コメント文字
  * `dlm::Function`: 指定された文字が区切り文字であるかどうかを示す関数。
