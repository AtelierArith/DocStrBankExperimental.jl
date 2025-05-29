```
equation_of_time(t::Union{Number, DateTime})
```

太陽の見かけの地方時と太陽の平均地方時の差 [rad] を計算します。これを時間 `t` で表される時間における時間の方程式と呼びます。アルゴリズムは **[1, p. 178, 277-279]** から適応されました。

# 参考文献

  * **[1]** Vallado, D. A (2013). Fundamentals of Astrodynamics and Applications. 4th ed.   Microcosm Press, Hawthorne, CA.
