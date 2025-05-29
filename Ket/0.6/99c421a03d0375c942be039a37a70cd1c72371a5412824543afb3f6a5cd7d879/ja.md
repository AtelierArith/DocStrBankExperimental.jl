```
shiftclock(v::AbstractVector, p::Integer, q::Integer)
```

X^`p` * Z^`q` * `v` を生成します。ここで、X と Z は次元 length(`v`) のシフト演算子とクロック演算子です。

参考文献: [Generalized Clifford algebra](https://en.wikipedia.org/wiki/Generalized_Clifford_algebra)
