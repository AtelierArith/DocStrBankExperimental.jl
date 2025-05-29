```
@nvmon group_or_groups codeblock
```

参照: [`nvmon`](@ref)

**注意: これは実験的な機能であり、いつでも変更または削除される可能性があります！**

# 例

```
julia> using LIKWID

julia> x = CUDA.rand(1000); y = CUDA.rand(1000);

julia> metrics, events = @nvmon "FLOPS_DP" x .+ y;
```
