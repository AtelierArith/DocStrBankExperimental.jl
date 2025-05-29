```
SeparableSum(f_1, ..., f_k)
```

関数 `f_1` から `f_k` までを与えると、それらの分離可能な和を返します。すなわち、

$$
g(x_1, ..., x_k) = \sum_{i=1}^k f_i(x_i).
$$

このように構築されたオブジェクト `g` は、長さ `k` の `Tuple` で評価できます。同様に、`g` の `prox` および `prox!` メソッドは、長さ `k` の `Tuple` で (入力と出力) 操作します。

例:

```
f = SeparableSum(NormL1(), NuclearNorm()); # 2つの関数の分離可能な和
x = randn(10); # 一部のランダムベクトル
Y = randn(20, 30); # 一部のランダム行列
f_xY = f((x, Y)); # (x, Y) で f を評価
(u, V), f_uV = prox(f, (x, Y), 1.3); # (x, Y) で prox を計算
```
