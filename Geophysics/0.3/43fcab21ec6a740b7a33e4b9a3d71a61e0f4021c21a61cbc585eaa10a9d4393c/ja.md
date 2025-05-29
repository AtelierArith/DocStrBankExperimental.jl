```
onreedom(h::Real=0,W::Weather) = freedom(temperature(h,W),fluid(W))
```

高度 `h` における自由度 `f` は、天候の場所（無次元）です。
