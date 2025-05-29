```
Dictionary{I,T}(;sizehint = 8)
```

空のハッシュベースの辞書を構築します。`I` と `T` は指定されていない場合、デフォルトで `Any` になります。`sizehint` を指定することでハッシュテーブルの初期サイズを設定でき、これによりその後の `insert!` 操作が高速化される可能性があります。

# 例

```julia
julia> d = Dictionary{Int, Int}()
0-element Dictionary{Int64,Int64}
```
