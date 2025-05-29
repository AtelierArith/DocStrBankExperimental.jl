```
GenerateFromPasswordは、指定されたコストでのパスワードのbcryptハッシュを返します。
指定されたコストが`MinCost`未満の場合、コストは代わりに`DefaultCost`に設定されます。
このパッケージで定義されている`CompareHashAndPassword`を使用して、返されたハッシュ化されたパスワードとその平文バージョンを比較します。
```
