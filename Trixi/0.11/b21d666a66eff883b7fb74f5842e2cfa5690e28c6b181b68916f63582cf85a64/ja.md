```
velocity(u, equations)
```

方程式に対応する速度ベクトルを返します。例えば、オイラー方程式に対する流体の速度です。特定の方向または法線方向における速度（スカラー）は、`velocity(u, orientation, equations)` または `velocity(u, normal_direction, equations)` を使用して計算できます。それぞれの関数 `velocity(u, normal_direction, equations)` は、速度ベクトルを計算するために `velocity(u, equations)` を呼び出し、その後法線ベクトルを計算します。これにより、AbstractEquations型の一般的な関数を記述できるようになります。しかし、`velocity(u, orientation, equations)` は、望ましい方向（オリエンテーション）における速度のみが計算されることを保証するために、各方程式ごとに記述されています。`u` は、単一のノードにおける保存変数のベクトルであり、すなわち `nvariables(equations)` の正しい長さのベクトルです。
