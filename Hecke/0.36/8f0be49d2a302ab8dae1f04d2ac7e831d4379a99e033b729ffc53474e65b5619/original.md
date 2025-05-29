```
isomorphism_data(f::EllCrvIso) -> (T, T, T, T)
```

Return the tuple $(r, s, t, u)$ that defines the isomorphism which is of the form [x : y : 1] -> [(x - r)//u^2 : (y - s*(x-r) - t)//u^3 : 1]
