```
Game{T} <: AbstractGame{T}
```

プレイヤーIDタイプが `T` のゴーフィッシュゲームオブジェクトです。

# フィールド

  * `deck`: カードのデッキ
  * `book`: プレイヤーIDとカードの値を含む辞書:  `id => value`
  * `hand_size`: 各プレイヤーの手札の最大枚数
