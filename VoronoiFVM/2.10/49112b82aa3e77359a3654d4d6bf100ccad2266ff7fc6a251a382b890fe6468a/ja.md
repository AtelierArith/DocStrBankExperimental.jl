```
integrate(system,tf, Ut; rate=true, params, data)
```

過渡解のためのテスト関数の積分を計算します。`rate=true`（デフォルト）の場合、対応する境界を通過する流量（毎秒）を計算します。それ以外の場合は、絶対量を計算します。結果は `nspec x (nsteps-1)` の DiffEqArray です。
