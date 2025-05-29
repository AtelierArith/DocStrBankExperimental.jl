```
struct HierarchyDict <: AbstractHierarchyDict
```

純粋（ボソンまたはフェルミオン）バス-ADO階層のすべての辞書を含むオブジェクトです。

# フィールド

  * `idx2nvec` : 与えられたADOのインデックスから`Nvec`を返します
  * `nvec2idx` : 与えられた`Nvec`からADOのインデックスを返します
  * `lvl2idx` : 与えられた階層レベルからADOインデックスのリストを返します
  * `bathPtr` : `Nvec`の各位置に対してタプル$(\alpha, k)$を記録し、ここで$\alpha$と$k$は$\alpha$-thバスの$k$-th指数展開項を表します。
