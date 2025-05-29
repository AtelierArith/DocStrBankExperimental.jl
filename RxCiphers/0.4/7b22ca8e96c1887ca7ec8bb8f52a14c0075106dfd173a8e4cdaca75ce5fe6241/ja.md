```
checktoken(token::Int, W::AbstractCharSpace)
```

トークンが `W` に存在しない場合は `ArgumentError` をスローし、そうでなければ `token` を返します。
