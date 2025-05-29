```
FalsePosition([galadino_factor])
```

[false position](https://en.wikipedia.org/wiki/False_position_method) 法を使用して、区間 `[a,b]` 内の関数 `f` のゼロを見つけます。

false position 法は修正された二分法であり、`[aₖ, bₖ]` の中点は、2点間の平均ではなく、セカント線が $x$ 軸と交差する点として選ばれます。

凹関数の収束を速めるために、このアルゴリズムは Galdino の $12$ の減少因子を実装しています (*A family of regula falsi root-finding methods*)。これらは、`FalsePosition(2)` のように数で指定するか、`FalsePosition(:pegasus)`、`FalsePosition(:illinois)`、または `FalsePosition(:anderson_bjork)` のいずれかの名前で指定します（デフォルト）。デフォルトの選択は一般的に他のものよりもパフォーマンスが良いですが、例外もあります。

いくつかの問題では、関数呼び出しの数が `Bisection` 法よりも多くなることがありますが、一般的にこのアルゴリズムはより少ない関数呼び出しを行います。

例

```
find_zero(x -> x^5 - x - 1, (-2, 2), FalsePosition())
```
