```
ChromeDevToolsLite
```

Chrome DevTools Protocol クライアントの軽量な Julia 実装。

# 機能

  * Chrome DevTools Protocol を介したブラウザの自動化と制御
  * 要素の操作と操作
  * ページのナビゲーションと JavaScript の評価
  * スクリーンショットのキャプチャ

# 設定

すべての関数は、ログ出力を制御するために `verbose` フラグを受け入れます：

  * `verbose=true`: @info および @debug メッセージを含む詳細なログを有効にします
  * `verbose=false` (デフォルト): 情報ログを抑制します

例：

```julia
client = connect_browser(verbose=true)
element = ElementHandle(client, "#my-button", verbose=true)
click(element)
```
