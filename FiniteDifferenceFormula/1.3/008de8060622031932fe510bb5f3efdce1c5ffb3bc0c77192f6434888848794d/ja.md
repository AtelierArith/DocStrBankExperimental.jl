`formula`()

生成してリストします：

1. `k[1]*f(x[i+points[1]]) + k[2]*f(x[i+points[2]]) + ... + k[len]*f(x[i+points[len]])     = m*f^(n)(x[i]) + ..., m > 0`
2. f^(n)(x[i]) の公式、精度の推定をビッグ-O 表記で含む。
3. f^(n)(x[i]) のための Julia 関数。

`compute(n, points, true)` を呼び出すことは、`compute(n, points)` を呼び出してから `formula()` を呼び出すのと同じです。

公式が見つからなくても、なぜそうなのかを見ることができる計算結果をリストします。例えば、`compute(2,1:2)` の後に `formula()` を試してください。
