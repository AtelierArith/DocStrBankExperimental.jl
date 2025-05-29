```
moving(f, ta::TimeArray{T,1}, w::Integer; padding = false)
```

ユーザー定義関数 `f` をウィンドウサイズ `w` の 1D `TimeArray` に適用します。

## 例

時系列の単純移動平均を計算するには：

```julia
moving(mean, ta, 10)
```
