```
moving(f, ta::TimeArray{T,2}, w::Integer; padding = false, dims = 1, colnames = [...])
```

## 例

`dims = 2` の場合、ユーザー定義関数 `f` は 2D `Array` を入力として受け取ります。

```julia
moving(ohlc, 10, dims = 2, colnames = [:A, ...]) do
    # `ohlc` が 500x4 の `TimeArray` であると仮定すると、
    # size(A) は (10, 4) です
    ...
end
```
