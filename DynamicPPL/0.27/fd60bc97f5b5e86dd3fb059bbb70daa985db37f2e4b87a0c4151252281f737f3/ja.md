```
conditioned(context::AbstractContext)
```

`context`に基づいて条件付けされた値の`NamedTuple`を返します。

これは、コンテキストスタックを再帰的にトラバースし、条件値のマージされたバージョンを返すことに注意してください。
