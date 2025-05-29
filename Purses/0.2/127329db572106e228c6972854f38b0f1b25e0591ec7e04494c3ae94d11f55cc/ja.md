```
Purse(value, fs...)
```

`value`を`Purse`でラップして返します。`fs`の各`f`は、呼び出し可能なものか、呼び出し可能なものと値のペアのいずれかです。`f`が呼び出し可能なものであれば、キャッシュは自動的に`value`に各`f`を適用することで計算されます。`f`がペアであれば、ペアの最初の要素のキャッシュは、第二の要素の値に設定されます。

# 例

```jldoctest
julia> Purse(1.0)
Purse{Float64,Tuple{},Tuple{}}(1.0, ())

julia> Purse(2, inv)
Purse{Int64,Tuple{typeof(inv)},Tuple{Float64}}(2, (0.5,))

julia> Purse(2, inv => 0.2)
Purse{Int64,Tuple{typeof(inv)},Tuple{Float64}}(2, (0.2,))
```
