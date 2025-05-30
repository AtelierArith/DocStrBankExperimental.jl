limit(pool::Pool{T}) where T -> Int

プールが同時に保持できるリソースの最大数を返します。

この関数はプールの`limit`を返し、これは任意の時点で使用中（取得中）であることができるリソースの最大数を表します。

# 引数

  * `pool::Pool{T}`: クエリするリソースプール。

# 戻り値

プールによって許可される同時リソースの最大数。

# スレッドセーフ

この操作はスレッドセーフです。`pool.limit`フィールドへのアクセスは、Juliaでは本質的に原子的です。

# 例

```julia
using Pools

create(::Type{Int}) = rand(1:10)

pool = GenericPool{Int}(5)
limit(pool)
```
