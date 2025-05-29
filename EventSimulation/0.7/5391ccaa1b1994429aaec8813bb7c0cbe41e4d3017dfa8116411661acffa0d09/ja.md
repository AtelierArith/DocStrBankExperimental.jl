```
waive!(r, res_request)
waive!(q, request)
```

`res_request`を`SimResource`から、または`request`を`SimQueue`から削除する最初の発生を取り除くことを許可します。

成功した場合は`true`を返し、`res_request`または`request`がそれぞれ見つからなかった場合は`false`を返します。
