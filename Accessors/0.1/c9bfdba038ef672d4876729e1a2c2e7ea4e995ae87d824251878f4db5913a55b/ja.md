```
@accessor func
```

シンプルなゲッタ関数を与えられた場合、対応する `set` メソッドを自動的に定義します。

# 例

```julia
julia> @accessor my_func(x) = x.a

julia> my_func((a=1, b=2))
1

julia> set((a=1, b=2), my_func, 100)
(a = 100, b = 2)
```
