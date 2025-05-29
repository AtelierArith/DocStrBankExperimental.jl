```
stan_dump(filename, data; force = false, kwargs...)
stan_dump(io, data; kwargs...)
stan_dump(StanDump.StanDumpIO(io; kwargs...), data)
```

`data`を書き込みます。これは`pairs`をサポートする値（例えば`NamedTuple`や`Dict`）です。

`filename`を使用する場合、`force = true`が指定されない限り上書きされることはありません。

キーワード引数は`StanDumpIO`に渡され、フォーマットを制御します（ほとんどのユーザーはこれを気にする必要はありませんが、デバッグ目的で使用されます）。

# 例

```jldoctest
julia> stan_dump(stdout, (N = 1, a = 1:5, b = ones(2, 2)))
N <- 1
a <- 1:5
b <- structure(c(1.0, 1.0, 1.0, 1.0), .Dim = c(2, 2))
```
