```
Ok(value::T) -> ok::Ok{T}
Ok{T}(value) -> ok::Ok{T}
Ok() -> Ok(nothing)
```

`value`は、この値を返すAPIによって定義された意味での「成功」を示します。

参照: [`isok`](@ref), [`unwrap`](@ref)

# 例

```jldoctest Ok
julia> using Try

julia> result = Ok(1)
Try.Ok: 1

julia> Try.unwrap(result)
1
```
