```
Dictionary(indexable)
Dictionary{I}(indexable)
Dictionary{I,T}(indexable)
```

インデックス可能な入力 `indexable` からハッシュベースの辞書を構築します。これは `Dictionary(keys(indexable), values(indexable))` と同等です。入力はコピーされない場合があります。

注意: `Pair` から辞書を構築するには `dictionary` 関数を使用してください。`index` 関数も参照してください。

# 例

```julia
julia> Dictionary(Dict(:a=>1, :b=>2))
2-element Dictionary{Symbol,Int64}
 :a │ 1
 :b │ 2

julia> Dictionary(3:-1:1)
3-element Dictionary{Int64,Int64}
 1 │ 3
 2 │ 2
 3 │ 1 
```
