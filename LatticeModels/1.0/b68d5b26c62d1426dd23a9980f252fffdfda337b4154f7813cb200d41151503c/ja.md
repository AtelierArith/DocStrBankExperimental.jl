```
FunctionBoundary <: Boundary
```

与えられたサイトの位相因子を返す関数を持つ境界条件。境界条件は $ψ(x + R) = f(x)ψ(x)$ の形でエンコードされており、ここで $f(x)$ は関数、$R$ は平行移動ベクトルです。

---

```
FunctionBoundary(f, translation)
```

与えられた関数と平行移動を持つ `FunctionBoundary` を構築します。

## 引数

  * `f`: 与えられたサイトの位相因子を返す関数。
  * `translation`: `AbstractTranslation` として表現された境界の平行移動ベクトル。配列が渡された場合、自動的に `Translation` に変換されます。
