```
is_point(M::ValidationManifold, p; kwargs...)
```

[`is_point`](@ref)を[`ValidationManifold`](@ref)上で実行します。この呼び出しに使用できる2つの追加キーワードがあります。

  * `within=nothing`は、この呼び出しが発行された関数を指定します。
  * `context::NTuple{N,Symbol} where N=()`は、この呼び出しが発行された1つ以上のコンテキストを指定します。テストを実行すべきかどうかを確認する前に、コンテキスト`:Point`が追加されます。

その他のすべてのキーワードはそのまま渡されます。
