```
get_vector(wv, word [; oov=false, oov_key="<unk>")
```

`wv`から`word`のベクトル表現を返します。`oov`が`true`の場合、語彙外の単語に対しては`oov_key`に対応するベクトルが返されます。
