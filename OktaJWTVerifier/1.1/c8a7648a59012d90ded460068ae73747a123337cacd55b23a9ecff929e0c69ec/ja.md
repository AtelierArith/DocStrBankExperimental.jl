```
verify_access_token!(j::Verifier, jwt::String)
```

与えられた Verifier を使用して、指定されたアクセストークンを検証します。Verifier はアクセストークンと同じ発行者で作成されている必要があります。アクセストークンは有効な JWT であり、Verifier と同じ発行者によって発行されている必要があります。また、アクセストークンは Verifier コンストラクタに渡された claims*to*validate に従って有効である必要があります。

アクセストークンのクレームを含む Jwt オブジェクトを返します。
