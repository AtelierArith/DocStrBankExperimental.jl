```
get_order(genpoly::Polynomial{F}) where F <: GaloisFields.AbstractGaloisField
```

多項式の次数を計算します。

# 引数

  * `genpoly::Polynomial{F}`: 有限体上の多項式

# 戻り値

  * `Int`: 多項式の次数

# 例

```julia
F2 = @GaloisField 2
p = Polynomial([F2(1), F2(1), F2(1)])  # x^2 + x + 1
get_order(p)  # 3
```
