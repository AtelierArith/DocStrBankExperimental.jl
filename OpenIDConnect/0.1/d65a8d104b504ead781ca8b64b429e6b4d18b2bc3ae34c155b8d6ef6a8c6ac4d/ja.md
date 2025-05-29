トークンリクエスト。取得した認証コードを使用して、トークンエンドポイントを呼び出し、id*token、access*token、refresh*tokenを取得します。詳細は https://openid.net/specs/openid-connect-core-1*0.html のセクション3.1.3.1を参照してください。

成功した場合、トークンを含むJSONオブジェクトを返します。失敗した場合は、AuthServerErrorまたはAPIErrorオブジェクトを返します。
