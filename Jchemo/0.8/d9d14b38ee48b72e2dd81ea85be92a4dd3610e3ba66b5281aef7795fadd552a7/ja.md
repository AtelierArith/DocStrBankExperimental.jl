```
vcatdf(dat; cols = :intersect)
```

データフレームのリストの垂直連結。

  * `dat` : データフレームのリスト（ベクター）。
  * `cols` : 返されるデータフレームの列を決定します。   詳細は ?DataFrames.vcat を参照してください。

## 例

```julia
using Jchemo, DataFrames

dat1 = DataFrame(rand(5, 2), [:v3, :v1]) 
dat2 = DataFrame(100 * rand(2, 2), [:v3, :v1])
dat = (dat1, dat2)
Jchemo.vcatdf(dat)

dat2 = DataFrame(100 * rand(2, 2), [:v1, :v3])
dat = (dat1, dat2)
Jchemo.vcatdf(dat)

dat2 = DataFrame(100 * rand(2, 3), [:v3, :v1, :a])
dat = (dat1, dat2)
Jchemo.vcatdf(dat)
Jchemo.vcatdf(dat; cols = :union)
```
