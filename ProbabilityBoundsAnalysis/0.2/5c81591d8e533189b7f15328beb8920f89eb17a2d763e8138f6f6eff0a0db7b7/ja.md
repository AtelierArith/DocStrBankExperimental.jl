```
normal(mean :: Interval, std :: Interval)
```

正規分布の形をしたpbox。パラメータは実数または区間で指定できます。

# コンストラクタ

  * `normal`
  * `N`
  * `gaussian`

# 例

```jldoctest
julia> a = normal(interval(0, 1), interval(1,2))
Pbox: 	  ~ normal ( range=[-6.1805, 7.1805], mean=[0.0, 1.0], var=[1.0, 4.0])
```

参照: [`uniform`](@ref), [`lognormal`](@ref), [`meanMinMax`](@ref), [`plot`](@ref)
