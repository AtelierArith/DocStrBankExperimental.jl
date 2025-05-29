```
register_bivariate(f, df1, df2, ddf11, ddf12, ddf22)
```

バイバリアント関数 `f` を `ExaModels` に登録し、目的関数および制約式内で使用できるようにします。

# 引数:

  * `f`: 関数
  * `df1`: 第一引数に関する導関数
  * `df2`: 第二引数に関する導関数
  * `ddf11`: 第一引数に関する二次導関数
  * `ddf12`: 第一引数および第二引数に関する二次導関数
  * `ddf22`: 第二引数に関する二次導関数

## 例

```jldoctest
julia> using ExaModels

julia> relu23(x) = (x > 0 || y > 0) ? (x + y)^3 : zero(x)
relu23 (generic function with 1 method)

julia> drelu231(x) = (x > 0 || y > 0) ? 3 * (x + y)^2 : zero(x)
drelu231 (generic function with 1 method)

julia> drelu232(x) = (x > 0 || y > 0) ? 3 * (x + y)^2  : zero(x)
drelu232 (generic function with 1 method)

julia> ddrelu2311(x) = (x > 0 || y > 0) ? 6 * (x + y) : zero(x)
ddrelu2311 (generic function with 1 method)

julia> ddrelu2312(x) = (x > 0 || y > 0) ? 6 * (x + y) : zero(x)
ddrelu2312 (generic function with 1 method)

julia> ddrelu2322(x) = (x > 0 || y > 0) ? 6 * (x + y) : zero(x)
ddrelu2322 (generic function with 1 method)

julia> @register_bivariate(relu23, drelu231, drelu232, ddrelu2311, ddrelu2312, ddrelu2322)
```
