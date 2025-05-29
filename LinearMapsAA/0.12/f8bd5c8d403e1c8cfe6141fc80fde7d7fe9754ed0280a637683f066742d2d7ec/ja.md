```
B = LinearMapAO(A::LinearMapAX)
```

AMからAOを作成しますが、`idim`と`odim`が1Dであるにもかかわらず、`B*X`が`Array`になることを望むエキスパートユーザー向けです。`undim`の逆のようなものです。
