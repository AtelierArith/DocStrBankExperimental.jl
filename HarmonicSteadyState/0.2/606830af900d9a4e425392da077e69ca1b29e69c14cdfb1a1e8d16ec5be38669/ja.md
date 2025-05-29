```
ポリヘドラル
```

ポリヘドラルホモトピー法は、ポリノミアルシステムのポリヘドラル構造に基づいてホモトピーを構築します。これは、係数のほとんどがゼロであるスパースシステムに対して、トータルディグリーメソッドよりも効率的です。ゼロ解を見つける必要がない場合（`only_non_zero = true`）、特に有用であり、速度が向上します。詳細については、[HomotopyContinuation.jl](https://www.juliahomotopycontinuation.org/guides/polyhedral/)を参照してください。

# フィールド

  * `only_non_zero::Bool`: ゼロでない解のみを考慮するかどうかを示すブール値。
  * `thread::Bool`: スレッディングが有効かどうかを示すブール値。
  * `tracker_options::HomotopyContinuation.TrackerOptions`: トラッカーのオプション。
  * `endgame_options::HomotopyContinuation.EndgameOptions`: エンドゲームのオプション。
  * `compile::Union{Bool, Symbol}`: コンパイルオプション。
  * `seed::UInt32`: 乱数生成のためのシード。
