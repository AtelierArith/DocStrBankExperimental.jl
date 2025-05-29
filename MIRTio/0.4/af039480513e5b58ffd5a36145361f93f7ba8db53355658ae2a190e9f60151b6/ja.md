```
ht = header_string(ht::NamedTuple ; strip::Bool)
```

NamedTuple内の各`Array{Cuchar}`を`String`に変換

in

  * `ht::NamedTuple`は`header_init()`または`header_read()`から

option

  * `strip::Bool`は文字列から末尾の空白文字を削除しますか？デフォルトは`false`

out

  * `ht::NamedTuple`
