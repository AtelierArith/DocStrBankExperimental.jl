```
crop_mask(
    x::AbstractArray,
    m::AbstractArray = x;
    out = 0
) -> typeof(x[...])
```

マスクに基づいて配列を切り抜きます。

### 引数

  * `x::AbstractArray`: 切り抜く配列
  * `m::AbstractArray`: マスク

### キーワード

  * `out = 0`: `m`内で外部と見なされる値

### 戻り値

  * `typeof(x[...])`: 切り抜かれた配列
