Bitly APIへの接続。

## コンストラクタ

  * `BitlyToken()`: トークンが自動的に検出されます。最初に、環境変数

`BITLY_ACCESS_TOKEN`を探し、その後`~/.bitlyrc`ファイルを探します。

  * `BitlyToken(token::AbstractString)`: ユーザーがトークンを直接指定します。

[`requestBitlyToken`](@ref)を参照してください。
