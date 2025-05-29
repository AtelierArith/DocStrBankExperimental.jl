```
ForcingTerm
```

`rtol[n]`の値をニュートン-クライロフ法のために計算します。これは、`get_rtol!(::ForcingTerm, cache, f, n)`を呼び出すことで行われ、`rtol[n]`を返します。`cache`は、`allocate_cache(::ForcingTerm, x_prototype)`を使用して取得でき、`x_prototype`は`f`に似ています。

強制項とその収束保証についての詳細な議論は、S.C. EisenstatとH.F. Walkerによる「Choosing the Forcing Terms in an Inexact Newton Method」を参照してください（http://softlib.rice.edu/pub/CRPC-TRs/reports/CRPC-TR94463.pdf）。
