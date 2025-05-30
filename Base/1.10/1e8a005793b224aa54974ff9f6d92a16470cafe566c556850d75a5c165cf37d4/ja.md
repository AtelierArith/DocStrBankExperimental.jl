```
findmin(f, domain) -> (f(x), index)
```

`f`の出力値（コドメイン内の値）と、`domain`内の対応する値のインデックス（`f`への入力）をペアで返します。`f(x)`が最小化されるような値を返します。最小点が複数ある場合は、最初のものが返されます。

`domain`は空でないイテラブルでなければなりません。

`NaN`は、`missing`を除くすべての他の値よりも小さいと見なされます。

!!! compat "Julia 1.7"
    このメソッドはJulia 1.7以降が必要です。


# 例

```jldoctest
julia> findmin(identity, 5:9)
(5, 1)

julia> findmin(-, 1:10)
(-10, 10)

julia> findmin(first, [(2, :a), (2, :b), (3, :c)])
(2, 1)

julia> findmin(cos, 0:π/2:2π)
(-1.0, 3)
```
