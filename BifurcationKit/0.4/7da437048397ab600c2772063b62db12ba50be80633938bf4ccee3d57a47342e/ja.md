```
ムーア・ペンローズ予測/修正
```

ムーア・ペンローズ継続アルゴリズム。

追加情報は[ウェブサイト](https://bifurcationkit.github.io/BifurcationKitDocs.jl/dev/MooreSpence/)で入手できます。

# コンストラクタ

`alg = MoorePenrose()`

`alg = MoorePenrose(tangent = PALC())`

# フィールド

  * `tangent::Any`: 接線予測子、例えば `PALC()`
  * `method::BifurcationKit.MoorePenroseLS`: ムーア・ペンローズ線形ソルバー。BifurcationKit.direct、BifurcationKit.pInv、またはBifurcationKit.iterativeのいずれか
  * `ls::BifurcationKit.AbstractLinearSolver`: （境界付き）線形ソルバー
