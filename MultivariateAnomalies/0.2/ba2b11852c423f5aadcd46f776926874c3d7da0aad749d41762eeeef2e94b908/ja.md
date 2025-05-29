```
EWMA!(Z, dat,  λ)
```

事前に割り当てられた出力 Z を使用します。 `Z = similar(dat)` または `dat = dat` で自分自身を上書きします。

# 例

```
julia> dc = rand(100,3,2)
julia> EWMA!(dc, dc, 0.1)
```
