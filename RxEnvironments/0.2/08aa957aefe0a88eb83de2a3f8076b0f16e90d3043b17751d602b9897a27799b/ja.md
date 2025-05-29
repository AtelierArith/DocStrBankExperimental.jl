```
add!(first::AbstractEntity{T,S,E}, second; environment=false) where {T,S,E}
```

`second`を`first`に追加します。`environment`が`true`の場合、`second`のために作成された`AbstractEntity`は環境としてラベル付けされます。両方のエンティティのマルコフブランケットは互いにサブスクライブされます。

# 引数

  * `first::AbstractEntity{T,S,E}`: `second`が追加されるエンティティ。
  * `second`: `first`に追加されるエンティティ。
  * `is_active=false`: `second`がアクティブエンティティとしてインスタンス化されるべきかどうかを示すブール値。
