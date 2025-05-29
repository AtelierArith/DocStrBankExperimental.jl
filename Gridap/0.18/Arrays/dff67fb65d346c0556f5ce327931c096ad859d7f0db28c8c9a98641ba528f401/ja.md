```
getindex!(cache,a::AbstractArray,i...)
```

インデックス `i` に関連付けられた配列 `a` のアイテムを、`cache` オブジェクトに渡されたスクラッチデータを使用して（可能であれば）返します。

デフォルトでは

```
getindex!(cache,a::AbstractArray,i...) = a[i...]
```

標準の Julia 配列に関しては、ユーザーは配列の `IndexStyle` に応じて、次のシグネチャのいずれかを実装する必要があります。

```
getindex!(cache,a::AbstractArray,i::Integer)
getindex!(cache,a::AbstractArray{T,N},i::Vararg{Integer,N}) where {T,N}
```

# 例

`getindex!` 関数を使用して配列を反復処理する

```jldoctest
using Gridap.Arrays

a = collect(10:15)

cache = array_cache(a)
for i in eachindex(a)
  ai = getindex!(cache,a,i)
  println("$i -> $ai")
end

# 出力
1 -> 10
2 -> 11
3 -> 12
4 -> 13
5 -> 14
6 -> 15
```
