```
cip_vector(m::IERSModel, tt_c::Number)
```

天体中間極（CIP）ベクトルを計算します。これは、IERSの規約 `m` に従い、時刻 `tt_c` において、J2000 からの `TT` ジュリア世紀で表現されます。

### 参考文献

  * Wallace P. T. と Capitaine N. (2006), IAU 2006 の決議に一致する歳差- nutation 手続き, [DOI: 10.1051/0004-6361:20065897](https://www.aanda.org/articles/aa/abs/2006/45/aa5897-06/aa5897-06.html)

### 参照

[`cip_xy`](@ref) も参照してください。
