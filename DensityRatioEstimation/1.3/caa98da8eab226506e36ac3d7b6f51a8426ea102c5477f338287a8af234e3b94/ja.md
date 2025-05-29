```
densratio(x_nu, x_de, dre; [optlib])
```

推定密度比 `p_nu(x_de) / p_de(x_de)` を推定器 `dre` と分子および分母サンプルのインデックス可能なコレクション `x_nu` と `x_de` を使用して行います。

オプションで、以下のリストから最適化ライブラリ `optlib` を選択できます：

  * `JuliaLib`  - 純粋なJulia実装
  * `OptimLib`  - Optim.jlを使用した実装
  * `ConvexLib` - Convex.jlを使用した実装
  * `JuMPLib`   - JuMP.jlを使用した実装

また、[`densratiofunc`](@ref)も参照してください。
