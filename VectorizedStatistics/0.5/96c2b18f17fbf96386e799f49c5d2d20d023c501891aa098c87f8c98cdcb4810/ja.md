```julia
vsort!([I], A; dims, multithreaded=false)
```

配列 `A` を、指定された次元 `dims` に沿ってオプションでソートします。

オプション引数 `I` が指定されている場合、`A` と同じ順序でソートされます。例えば、`I = collect(1:length(A))` の場合、`vsort!(I, A)` を呼び出した後、`A` はソートされ、`I` は `sortperm(A)` と等しくなります。

複数の `dims` にわたってソートする場合、これらの次元は連続している必要があります（つまり、`dims=(2,3)` は許可されますが、`dims=(1,3)` は許可されません）。また、`dims` に `:` 以外を指定すると、いくつかの非ゼロのパフォーマンスコストを伴う `view` が作成されることに注意してください。

## 例

```julia
julia> using VectorizedStatistics

julia> A = [1, 3, 2, 4];

julia> vsort!(A)
4-element Vector{Int64}:
 1
 2
 3
 4
```
