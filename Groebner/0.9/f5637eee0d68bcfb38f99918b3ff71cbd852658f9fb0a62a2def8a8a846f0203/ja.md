```
ProductOrdering(ord1, ord2)
```

積モノミアル順序。`ord1`で比較し、`ord2`で同点を解決します。

`*`を使って構築することもできます。

## 例

```@example
using Groebner, AbstractAlgebra
R, (x, y, z, w) = QQ["x", "y", "z", "w"];

# x, y > w, z の順序付け
ord = ProductOrdering(DegRevLex(x, y), DegRevLex(w, z))
groebner([x*y + w, y*z - w], ordering=ord)
```

`*`演算子を使用することも可能です：

```@example
using Groebner, AbstractAlgebra
R, (x, y, z, t) = QQ["x", "y", "z", "t"];

ord1 = Lex(t)
ord2 = DegRevLex(x, y, z)
# t >> x, y, z
ord = ord1 * ord2
groebner([x*y*z + z, t * z - 1], ordering=ord)
```
