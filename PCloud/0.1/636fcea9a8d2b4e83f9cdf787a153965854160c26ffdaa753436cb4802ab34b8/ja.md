```
authorize(client::PCloudClient; kwargs...)
```

これはOAuth 2.0認証フローを開始するウェブページです。このページでユーザーはpCloudにログインし、アプリへのアクセスを許可するかどうかを決定します。

ユーザーがアプリケーションに対してプロフィール情報や個人データへのアクセスを許可するかどうかの決定を下した後、`redirect_uri`で指定されたURIにリダイレクトされます。

OAuth 2.0には2つの異なる認証フローがあります：

*コードフロー* - `redirect_uri`リダイレクトを介して`code`を返します。このコードはその後、oauth2_tokenメソッドを使用して`bearer token`に変換する必要があります。

*トークン（暗黙的）フロー* - `redirect_uri`リダイレクトを介して`bearer token`を返します。これは、アプリがpCloud APIに対して2回目の呼び出しを開始する必要がありません。

*コードフロー*は、アプリがサーバーを使用している場合に推奨されます。

*トークンフロー*は、モバイルデバイスやJavaScriptのみに基づく純粋なクライアントサイドアプリに適しています。

出典: https://docs.pcloud.com/methods/oauth_2.0/authorize.html

# 引数

  * `client_id::String`: アプリのID。
  * `response_type::String`: codeまたはtoken。

# オプション引数

  * `redirect_uri::String`: 承認後にリダイレクトする場所。トークンには必須、コードにはオプション（この場合、コードはユーザーに表示されます）。
  * `state::String`: `redirect_uri`に戻される不透明なデータ。
  * `force_reapprove::Bool`: 設定されている場合、ユーザーによってアプリケーションがすでに承認されていても再承認を強制します。
  * `permissions::manageshares`: カンマ（,）で区切られたリスト。設定されている場合、追加の権限が承認フォームに表示されます。現在のところ唯一のオプションは

# 出力

承認後にリダイレクトされる先：

*コードフロー*

これらのパラメータはクエリ文字列に渡されます（?の後）

  * `code::String`: oauth2_tokenを呼び出すことでbearer tokenに交換できる認証コード。
  * `state::String`: 渡されたstateパラメータの内容。

redirect_uri?code=XXXXX&state=YYYYY

*トークンフロー*

これらのパラメータはURIフラグメントに渡されます（#の後）- `access_token::String`: pCloud APIメソッドを呼び出すために使用できるトークン。

  * `token_type::String`: トークンのタイプ（常にbearer）。
  * `uid::Int`: アプリへのアクセスを許可したユーザーのID。
  * `state::String`: 渡されたstateパラメータの内容。

redirect*uri#access*token=XXXXX&token_type=bearer&

uid=11111&state=YYYYYY ```
