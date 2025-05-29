```
modify!(f, dict::ConcurrentDict{K,V}, key::K) -> y
```

`dict`の`key`スロットを関数`f`を使用して原子的に更新します。

`key`が存在しない場合、`f`は`nothing`で呼び出されます。呼び出し`f(nothing)`は、スロットを空のままにするために(1) `nothing`を返すか、(2) `Some(value::V)`を返して`value`を挿入する必要があります。

`key`が存在する場合、`f`は`ref`で呼び出され、`ref[]`は`key`に対応する`value`を取得します。呼び出し`f(ref)`は、(1) スロットを削除するために`nothing`を返すか、(2) `value`を挿入するために`Some(value′::V)`を返すか、(3) [`Keep(ans)`](@ref ConcurrentCollection.Keep)を返して`modify!`から`y = Keep(ans)`を返すか、(4) [`Delete(ans)`](@ref ConcurrentCollection.Delete)を返してスロットを削除し、`modify!`から値`y = Delete(ans)`を返す必要があります。

関数`f`は、複数のタスクが辞書を変更しようとする場合、複数回呼び出されることがあります。

# 例

```jldoctest modify!
julia> using ConcurrentCollections

julia> dict = ConcurrentDict{String,Int}();

julia> modify!(dict, "hello") do _
           Some(1)
       end
Some(1)

julia> modify!(dict, "hello") do ref
           Some(something(ref[]) + 1)
       end
Some(2)
```
