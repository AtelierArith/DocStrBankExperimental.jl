```julia
DataDrivenAverageChainBehavior(data; fchain)

```

モデル:

  * 記事の補足資料に提供されたコードを適応したもの

パラメータ:

  * なし

フィールド:

  * `data`: 一軸の超弾性試験
  * `fchain(λch, pch)`: f(x, y) => f̂(x) = y の形の近似のためのコンストラクタ

> Amores VJ, Benítez JM, Montáns FJ. マクロスコピック実験データから得られた等方性不可圧縮ポリマーの平均鎖挙動。Julia言語におけるシンプルな構造ベースのWYPiWYGモデル。 Advances in Engineering Software. 2019年4月1日;130:41-57.


> Amores VJ, Benítez JM, Montáns FJ. データ駆動型、構造ベースの超弾性多様体: 鎖挙動を逆エンジニアリングし、ポリマーの効率的なシミュレーションを行うためのマクロ-ミクロ-マクロアプローチ。 Computers & Structures. 2020年4月15日;231:106209.

