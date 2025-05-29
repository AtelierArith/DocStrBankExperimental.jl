`Quoted(inner::AbstractToken; <kwargs>...)`

# 引数:

  * `inner`: 解析するための引用符内のトークン
  * `required`: 解析が成功するために引用符が必要ですか？デフォルトは`false`
  * `includequotes`: 出力に引用符を含める。デフォルトは`false`
  * `includenewlines`: 引用符内に現れる改行を含める。デフォルトは`true`
  * `quotechar`: 引用符に使用する文字（デフォルトは`LocalOpts`によって決定される）
  * `escapechar`: 引用符文字をエスケープする文字（デフォルトは`LocalOpts`によって設定される）
