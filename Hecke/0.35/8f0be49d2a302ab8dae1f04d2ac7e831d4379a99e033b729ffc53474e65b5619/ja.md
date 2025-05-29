```
isomorphism_data(f::EllCrvIso) -> (T, T, T, T)
```

タプル $(r, s, t, u)$ を返します。これは、形式 [x : y : 1] -> [(x - r)//u^2 : (y - s*(x-r) - t)//u^3 : 1] の同型を定義します。
