```
struct MixHierarchyDict <: AbstractHierarchyDict
```

混合（ボソンおよびフェルミオン）バス-ADO階層のすべての辞書を含むオブジェクトです。

# フィールド

  * `idx2nvec` : ADOの指定されたインデックスからタプル `(Nvec_b, Nvec_f)` を返します。ここで、`b` はボソンを、`f` はフェルミオンを表します。
  * `nvec2idx` : 指定されたタプル `(Nvec_b, Nvec_f)` からインデックスを返します。ここで、`b` はボソンを、`f` はフェルミオンを表します。
  * `Blvl2idx` : 指定されたボソニック階層レベルからADOインデックスのリストを返します。
  * `Flvl2idx` : 指定されたフェルミオン階層レベルからADOインデックスのリストを返します。
  * `bosonPtr` : `Nvec_b` の各位置に対してタプル $(\alpha, k)$ を記録します。ここで、$\alpha$ と $k$ は $\alpha$ 番目のボソンバスの $k$ 番目の指数展開項を表します。
  * `fermionPtr` : `Nvec_f` の各位置に対してタプル $(\alpha, k)$ を記録します。ここで、$\alpha$ と $k$ は $\alpha$ 番目のフェルミオンバスの $k$ 番目の指数展開項を表します。
