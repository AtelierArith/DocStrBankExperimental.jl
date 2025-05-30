```
uuid5(ns::UUID, name::String) -> UUID
```

RFC 4122で指定されたように、バージョン5（名前空間およびドメインベース）のユニバーサルユニーク識別子（UUID）を生成します。

!!! compat "Julia 1.1"
    この関数は少なくともJulia 1.1を必要とします。


# 例

```jldoctest
julia> rng = MersenneTwister(1234);

julia> u4 = uuid4(rng)
UUID("7a052949-c101-4ca3-9a7e-43a2532b2fa8")

julia> u5 = uuid5(u4, "julia")
UUID("086cc5bb-2461-57d8-8068-0aed7f5b5cd1")
```
