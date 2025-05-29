```
verify_id_token!(j::Verifier, jwt::String)
```

与えられた Verifier を使用して、指定された id トークンを検証します。Verifier は id トークンと同じ発行者で作成されている必要があります。id トークンは有効な JWT であり、Verifier と同じ発行者によって発行されている必要があります。また、id トークンは Verifier コンストラクタに渡された claims*to*validate に従って有効である必要があります。

id トークンのクレームを含む Jwt オブジェクトを返します。
