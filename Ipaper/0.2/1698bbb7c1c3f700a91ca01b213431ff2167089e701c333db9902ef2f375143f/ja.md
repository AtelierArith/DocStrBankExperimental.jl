```
par_map(f, A, args...; kw...)
```

# 例

```julia
function f(x)
  sleep(0.1)
  x
end

# get_clusters()
@time par_map(f, 1:10)
@time map(f, 1:10)
```
