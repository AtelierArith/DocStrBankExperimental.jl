```
get_authorization()::Authorization
```

認証トークンを取得します。この関数は最初に環境変数 `DROPBOXSDK_ACCESS_TOKEN` を探し、次に現在のディレクトリにあるファイル `secrets.http` を探します。どちらも存在しない場合、これはエラーです。
