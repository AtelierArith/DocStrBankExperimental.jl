```
@replicate n expr
```

式を `n` 回複製します

## 例

```julia
using DataConvenience, Random
@replicate 10 randstring(8) # 8文字のランダムな文字列を10個返します
```
