```
struct StandardDist{D<:Distribution{Univariate,Continuous},N} <: Distributions.Distribution{ArrayLikeVariate{N},Continuous}
```

`D()` または `D()` の積分布をディスパッチ可能な方法で表します。

コンストラクタ:

```
    StandardDist{Uniform}(size...)
    StandardDist{Normal}(size...)
```
