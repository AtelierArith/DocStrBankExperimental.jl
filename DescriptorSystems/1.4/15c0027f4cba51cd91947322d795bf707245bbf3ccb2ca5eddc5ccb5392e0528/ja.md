```
sys = rss(n, p, m; disc = false, Ts, T = Float64, stable = false, nuc = 0, nuo = 0, randt = true)
```

ランダム化された `n+nuc+nuo` 次の標準状態空間システム `sys = (A,B,C,D)` を生成します。出力は `p`、入力は `m` で、すべての行列は型 `T` のランダムに生成されたものです。`disc = false` の場合、結果の `sys` は連続時間システムであり、`disc = true` の場合は離散時間システムです。離散時間システムの場合、サンプル時間 `Δ` はキーワード引数 `Ts = Δ` を使用して指定できます（デフォルト: `Δ = -1`、すなわち指定なし）。

`stable = true` の場合、結果のシステムは安定しており、連続時間システムの場合は `A` のすべての固有値が負の実部を持ち、離散時間システムの場合は絶対値が1未満です。`nuc+nuo > 0` の場合、システム `sys` は非最小であり、`A` は `nuc` の制御不能な固有値と `nuo` の観測不能な固有値を持ちます。`randt = true` の場合、ランダムに生成された直交またはユニタリの相似変換が追加で適用されます。`randt = false` の場合、システム行列 `A`、`B`、および `C` は、`A` の制御不能および観測不能な固有値を示すブロック構造形式になります：

```
A = diag(A1, A2, A3),  B = [B1; 0; B3], C = [C1 C2 0]
```

対角ブロック `A1`、`A2`、`A3` の順序はそれぞれ `n`、`nuc`、`nuo` です。
