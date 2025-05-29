与えられた認証リクエストからのリダイレクトレスポンスのパラメータから、認可コードを抽出します。詳細は https://openid.net/specs/openid-connect-core-1_0.html のセクション 3.1.2.5 および 3.1.2.6 を参照してください。

成功した場合は認可コードを返します。失敗した場合は APIError または AuthServerError のいずれかを返します。
