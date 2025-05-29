```
convex_evaluator(::Num)
convex_evaluator(::Equation)
```

与えられた記号式または方程式に対して、式または方程式の右辺の凸緩和を評価する関数と、この新しい関数に渡すための正しい順序の引数のリストを返します。{下限、上限、凸緩和、凹緩和}のための評価関数を取得するには、`all_evaluators`を使用します。

# 例

代表的な使用例は次のとおりです：

```
@variables x, y
to_evaluate = 1 + x*y
evaluator, ordering = convex_evaluator(to_evaluate)
```

`to_evaluate`が`0 ~ 1 + x*y`のような方程式であっても同様のことが達成できますが、この関数にとってそのような方程式の左辺は無関係であることに注意することが重要です。この例では、「ordering」オブジェクトは、`evaluator`に渡すための正しい引数と引数の順序を示すベクトル`Num[xcc, xcv, xhi, xlo, ycc, ycv, yhi, ylo]`です。これらの引数の名前は、`to_evaluate`式で使用される変数に依存し、一般的には変数名に凸/凹値のための`cv`および`cc`が付加されたもの（すなわち、評価したい点）、変数の上限のための`hi`、および下限のための`lo`です。`x[1]`のような変数は、代わりに`x_1_cv`または同等のものとして表されます。

式の凸緩和は、特定の点`(x,y)`で評価できます。`x = xcv = xcc`および`y = ycv = ycc`とし、`x`および`y`の上限と下限をそれぞれ`xhi`、`yhi`、および`xlo`、`ylo`に設定します。例えば、`to_evaluate`の凸緩和をボックス`[0, 5]*[1, 3]`の点`(2.5, 2)`で評価するには、次のように入力できます：`evaluator(2.5, 2.5, 5.0, 0.0, 2.0, 2.0, 3.0, 1.0)`。

`evaluator`関数は、CuArraysを含むブロードキャストも可能です。例えば、GPUを使用してボックス`[0, 1]*[0, 1]`上の10,000のランダムな点で`to_evaluate`式の凸緩和を評価するには、次のように入力できます：

```
x_cv = CUDA.rand(Float64, 10000)
x_cc = CUDA.rand(Float64, 10000)
x_hi = CUDA.ones(Float64, 10000)
x_lo = CUDA.zeros(Float64, 10000)
y_cv = CUDA.rand(Float64, 10000)
y_cc = CUDA.rand(Float64, 10000)
y_hi = CUDA.ones(Float64, 10000)
y_lo = CUDA.zeros(Float64, 10000)
out = evaluator.(x_cc, x_cv, x_hi, x_lo, y_cc, y_cv, y_hi, y_lo)
as_array = Array(out)
```
