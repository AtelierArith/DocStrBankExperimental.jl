```
approximation_term(::CombinatorialInstance, ::CombinatorialAlgorithm)
```

このアルゴリズムが入力インスタンスで実行されたときの近似項を返します。問題が関数の最小化（例：最小コストパスの発見）の場合、項は次のように定義されます。定数 $t \ge 0.0$ （理想的には最小のもの）として

$$
f(x^\star) \leq f(x) \leq f(x^\star) + t,
$$

ここで $f(x^\star)$ は最適解のコストであり、$f(x)$ は返された解のコストです。逆に、最大化問題の場合、定義は逆になります（$t \ge 0.0$）：

$$
f(x^\star) \leq f(x) \leq f(x^\star) - t.
$$

正確なアルゴリズムの場合、項は常に $0.0$ であり、最小化問題と最大化問題の両方に対してそうです。

返される項は、アルゴリズムが定数項を提供する場合、定数である可能性があります。項が定数でない場合（すなわちインスタンス依存）、それは最悪の場合の値または真にインスタンス依存の項である可能性があります。アルゴリズムによっては、この動作は調整可能かもしれません。

アルゴリズムに保証がない場合、`NaN` を返すべきです。
