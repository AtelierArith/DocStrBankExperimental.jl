```
Err(value::E) -> err::Err{E}
Err{E}(value) -> err::Err{E}
```

`value`は、この値を返すAPIによって定義された意味での「失敗」を示します。

参照: [`iserr`](@ref), [`unwrap_err`](@ref)

# 例

```jldoctest Err
julia> using Try

julia> result = Err(1)
Try.Err: 1

julia> Try.unwrap_err(result)
1
```
