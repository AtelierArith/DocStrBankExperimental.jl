```
@alias alias_name real_name
```

このマクロは、`real_name` に設定された const 変数 `alias_name` を定義し、その関係を説明するドキュメント文字列を追加します。

さらに、`real_name` が現在のモジュールからエクスポートされている場合、`alias_name` もエクスポートされ、逆もまた然りです。これが機能するためには、`export` 文がこのマクロの呼び出しの前に来る必要があることに注意してください。

これは、`is_isomorphic` のようなエイリアスを提供するために使用できます（またはその逆）。`@deprecate` とは異なり、メソッドはどちらの名前の下でもインストールでき、2つの名前は実際には同じオブジェクトを指します。

# 例

```jldoctest; setup = :(using AbstractAlgebra) julia> foo(x::Int) = x

julia> @alias bar foo

julia> foo === bar true
```
