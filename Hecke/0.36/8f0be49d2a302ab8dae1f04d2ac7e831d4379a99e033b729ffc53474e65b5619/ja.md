```
isomorphism_data(f::EllCrvIso) -> (T, T, T, T)
```

返すタプル $(r, s, t, u)$ は、次の形の同型を定義します: [x : y : 1] -> [(x - r)//u^2 : (y - s*(x-r) - t)//u^3 : 1]
