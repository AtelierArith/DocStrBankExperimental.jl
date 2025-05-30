```markdown
taken(pool::Pool{T}) where T -> Int

プールから現在使用中のリソースの数を返します。

この関数は、プールから現在使用中（取得済み）のリソースがいくつあるかを確認するためのスレッドセーフな方法を提供します。これは、すぐに取得可能な自由なリソースは含まれません。

# 引数

  * `pool::Pool{T}`: クエリするリソースプール。

# 戻り値

プール内の取得済みリソースの数。

# スレッドセーフ

この操作はスレッドセーフです。

# 例

```

julia using Pools

create(::Type{Int}) = rand(1:10)

pool = GenericPool{Int}(3) taken(pool) ```
