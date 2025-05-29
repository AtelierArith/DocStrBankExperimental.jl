`verifyformula(n, points, k, m = 1)` または `activatejuliafunction(n, points, k, m = 1)`

数式が有効かどうかを確認します。有効な場合は、そのJulia関数を生成してアクティブにします。無効な場合は、ポイントを使用して導関数の数式を見つけようとします。

```
     n: n次導関数
points: 範囲の形式で、start : stop、またはリスト
     k: 数式の係数のリスト
     m: 数式の分母の係数
```

# 例

```julia-repl
import FiniteDifferenceFormula as fd
fd.verifyformula(1,[-1,2],[-3,4],5)  # f'(x[i]) = (-3f(x[i-1])+4f(x[i+2]))/(5h)?
fd.verifyformula(2, -3:3, [2,-27,270,-490,270,-27,2], 18)
fd.activatejuliafunction(2, -3:3, [1/90,-3/20,3/2,-49/18,3/2,-3/20,1/90])
fd.verifyformula(2, -3:3, [1//90,-3//20,3//2,-49//18,3//2,-3//20,1//90])
```
