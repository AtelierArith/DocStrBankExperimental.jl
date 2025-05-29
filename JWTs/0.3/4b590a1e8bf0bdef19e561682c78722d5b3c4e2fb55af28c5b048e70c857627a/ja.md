```
sign!(jwt, keyset, kid)
```

JWTをkeyset内のキーを使用して署名します。キーIDとキーアルゴリズムはJWTヘッダーに含まれます。JWTをヘッダーと署名で更新します。`nothing`を返します。

引数:

  * `jwt`: 署名するJWT。JWTがすでに署名されている場合は、再度署名されません。
  * `keyset`: 署名に使用するJWKSet。署名にはこのkeyset内のキーのみが使用されます。
  * `kid`: 署名に使用するキーID。keysetはJWTヘッダーからのキーIDを含む必要があります。そうでない場合はKeyErrorがスローされます。
