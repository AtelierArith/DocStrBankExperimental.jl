```
struct NonlinearCombinatorialInstance <: CombinatorialInstance
```

非線形組合せ最適化問題。こうした問題は線形問題 `combinatorial_structure` の上に構築され、問題に必要なすべての定数（例：グラフ）を提供します。このオブジェクトからの報酬は無視されます。最適化の感覚はこのオブジェクトによって与えられます（すなわち、最小化または最大化）。

非線形性は非線形目的関数にのみ含まれ、次のような表現を持つと想定されています：

$$
a^T x + f(b^T x)
$$

ここで、$a$ は `linear_coefficients` としてエンコードされ、$b$ は `nonlinear_coefficients` としてエンコードされます。関数 `f` は `nonlinear_function` によって示され、現在は列挙型 `NonlinearFunction` の値です。

`ε` は非線形インスタンスにしばしば使用されるパラメータで、問題が解決されるべき（加法的）精度を示します。
