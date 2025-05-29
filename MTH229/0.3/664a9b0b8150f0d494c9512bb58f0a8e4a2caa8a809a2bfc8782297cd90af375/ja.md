単純な二分法の実装。

例：

```julia
bisection(sin, 3, 4)
f(x) = x^5 - x^4 - x^3 - x^2 - x - 1
a = bisection(f, 1, 2)
f(a)
```

表示は、最初の数ステップの方法の分割を示す簡単なグラフィックを表示します。

`Roots.find_zero(f, (a,b), Bisection())`のより理解しやすい代替手段です。
