```
@register_univariate(f, df, ddf)
```

単変数関数 `f` を `ExaModels` に登録し、目的関数および制約式内で使用できるようにします。

# 引数:

  * `f`: 関数
  * `df`: 導関数
  * `ddf`: 二次導関数

## 例

```jldoctest
julia> using ExaModels

julia> relu3(x) = x > 0 ? x^3 : zero(x)
relu3 (generic function with 1 method)

julia> drelu3(x) = x > 0 ? 3*x^2 : zero(x)
drelu3 (generic function with 1 method)

julia> ddrelu3(x) = x > 0 ? 6*x : zero(x)
ddrelu3 (generic function with 1 method)

julia> @register_univariate(relu3, drelu3, ddrelu3)
```
