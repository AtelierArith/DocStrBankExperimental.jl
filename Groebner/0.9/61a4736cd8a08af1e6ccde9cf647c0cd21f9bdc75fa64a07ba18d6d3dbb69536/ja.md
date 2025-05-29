```
InputOrdering()
```

入力多項式に定義された単項式順序を保持します。

これは `ordering` キーワード引数のデフォルト値です。

## 例

```@example
using Groebner, AbstractAlgebra
R, (x, y) = QQ["x", "y"]

# `InputOrdering` を使用します。この場合、 
# x > y の辞書式順序がデフォルトとなります
groebner([x*y + x, x + y^2])
```
