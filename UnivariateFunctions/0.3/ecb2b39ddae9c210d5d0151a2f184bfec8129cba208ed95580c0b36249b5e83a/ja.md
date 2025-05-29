```
create_chebyshev_approximation(func::Function, nodes::Integer, degree::Integer, left::Real, right::Real)
```

別の関数をチェビシェフ多項式を用いて近似する関数です。

### 入力

  * `func` - 近似したい関数
  * `nodes` - 近似ノードの数
  * `degree` - チェビシェフ多項式の次数
  * `left` - 近似の左限界
  * `right` - 近似の右限界

### 返り値

  * 近似関数を含む `Sum_Of_Functions`。
