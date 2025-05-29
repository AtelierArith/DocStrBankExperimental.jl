```
AnsiTextCell
```

ANSIエスケープシーケンスのレンダリングをサポートし、テーブルのレイアウトに干渉しないテキストセルです。

# フィールド

**公開**

  * `string::String`: ANSIエスケープシーケンスを含む可能性のあるセルテキストの文字列。

**プライベート**

  * `_rendered_lines::Union{Nothing, Vector{String}}`: レンダリングされた文字列を含む行。
  * `_stripped_lines::Union{Nothing, Vector{String}}`: 印刷可能なテキストを含む行。
  * `_crops::Union{Nothing, Vector{Int}}`: 各行で切り取る必要がある文字数のベクター。
  * `_left_pads::Union{Nothing, Vector{Int}}`: 各行に適用される左パディング。
  * `_right_pads::Union{Nothing, Vector{Int}}`: 各行に適用される右パディング。
  * `_suffixes::Union{Nothing, Vector{String}}`: 各行に適用されるサフィックス。
