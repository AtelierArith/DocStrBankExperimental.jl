```
@alias alias_name real_name
```

このマクロは、`real_name` に設定された定数変数 `alias_name` を定義し、その関係を説明するドキュメント文字列を追加します。

さらに、`alias_name` は、`real_name` が現在のモジュールからエクスポートされている場合にエクスポートされ、逆もまた然りです。これが機能するためには、`export` 文がこのマクロの呼び出しの前に来る必要があります。

これは、`is_isomorphic` のための `isisomorphic` のようなエイリアスを提供するために使用できます（またはその逆）。`@deprecate` とは異なり、メソッドはどちらの名前の下でもインストールでき、2つの名前は実際には同じオブジェクトを指します。

エイリアスには、それがエイリアスであることを指摘する特別なドキュメント文字列も付与されます。

# 例

```jldoctest
julia> foo(x::Int) = x
foo (generic function with 1 method)

julia> @alias bar foo

julia> foo === bar
true
```
