```
ThreadLocalStorage{T}(factory)
ThreadLocalStorage(factory)
```

`factory()`によって作成された型`T`のスレッドローカルストレージを作成します。

`ThreadLocalStorage`のインスタンス`tls`は、値`T`のオブジェクト`x`を取得するための操作`x = tls[]`をサポートします。

!!! warning
    このAPIの使用は非常に難しいです。 いつ、どのように使用できるかは、議論の余地があります。

    理論的には、プログラマーが、値`x = tls[]`が取得された後、`x`へのアクセスがなくなるまでコードがいかなるイールドポイントにも達しないことを保証できる場合、このAPIを使用することは安全です。 しかし、特定の操作が一般的にイールドフリーであるかどうかを知ることは不可能です。

    したがって、このAPIは現在、`nthreads`および`threadid`をアドホックに使用して書かれたコードの移行を支援するために主に存在します。


Juliaランタイムの各ワーカースレッドに対して型`T`のオブジェクトが割り当てられます。 `T`が指定されていない場合、`T = typeof(factory())`が使用されます（すなわち、`factory`は型安定であると仮定されます）。

# 拡張ヘルプ

## 例

```jldoctest ThreadLocalStorage
julia> using ConcurrentUtils

julia> tls = ThreadLocalStorage(Ref{Int});

julia> tls[] isa Ref{Int}
true

julia> tls[][] = 123;

julia> tls[][]
123
```
