リダイレクトヘッダーを設定し、`Response`を準備します。3つのパラメータを受け取ります：1 - ルートのラベル（詳細については、詳細なルートセクションを参照してください） 2 - デフォルトのHTTP 302 Found ステータス：提供されたリソースが指定されたURLに変更されることを示します 3 - HTTPリクエストヘッダーを定義するためのタプル（キー、値）

例： julia> Genie.Renderer.redirect(:index, 302, Dict("Content-Type" => "application/json; charset=UTF-8"))

HTTP.Messages.Response: HTTP/1.1 302 Moved Temporarily Content-Type: application/json; charset=UTF-8 Location: /index

/indexにリダイレクトしています
