```
is_vector(M::ValidationManifold, p, X, cbp=true; kwargs...)
```

[`ValidationManifold`](@ref) に対して [`is_vector`](@ref) を実行します。この呼び出しに使用できる2つの追加キーワードがあります。

  * `within=nothing` は、この呼び出しが発行された関数を指定します。
  * `context::NTuple{N,Symbol} where N=()` は、この呼び出しが発行された1つ以上のコンテキストを指定します。テストを実行すべきかどうかを確認する前に、コンテキスト `:Point` が追加されます。

他のすべてのキーワードはそのまま渡されます。
