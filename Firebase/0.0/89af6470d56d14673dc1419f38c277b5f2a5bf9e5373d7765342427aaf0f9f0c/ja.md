```
initparsedjson( parsedjson)
```

SDKキーが解析されたJSON形式であり、ファイルがadminsdkkey.jsonとして保存されている場合に初期化します。

## 例

```md julia> r = HTTP.get(BASE_URL, header); # ヘッダーとボディを含むレスポンスを返します HTTP.Messages.Response

julia> response = JSON.json(JSON.parse(String(r.body))) "{"client*email":"****","client*id":"****","auth*uri":"https://accounts.google.com/o/oauth2/auth","auth*provider*x509*cert*url":"https://www.googleapis.com/oauth2/v1/certs","token*uri":"https://oauth2.googleapis.com/token","client*x509*cert*url":"https://www.googleapis.com/robot/v1/metadata/x509/firebase-adminsdk-jk50g%40volka-bot.iam.gserviceaccount.com","project*id":"volka-bot","type":"service*account","private*key":"****","private*key*id":"****"}"

julia> initparsedjson( response) プロジェクト Admin SDKキーはadminsdkkey.jsonになりました!! project*id: **** client*email: **** ````
