```
uniform(min :: Interval, max :: Interval)
```

一様な形状のpbox。パラメータは実数または区間であることができます。

# コンストラクタ

  * `uniform`
  * `U`

# 例

```jldoctest
julia> a = uniform(interval(0, 1), interval(1,2))
Pbox: 	  ~ uniform ( range=[0.0, 2.0], mean=[0.5, 1.5], var=[0.0, 0.33333])
```

参照: [`normal`](@ref), [`beta`](@ref), [`meanMinMax`](@ref), [`plot`](@ref)
