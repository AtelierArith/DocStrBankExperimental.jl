```
TabularModel([::Type,] num_states; num_outputs, num_actions)
```

タブラー モデルを作成します。これは、アイデンティティ基底関数を使用し、1つのタイルとタイルの数が状態の数に等しいタイルコーディングモデルの特別なケースです。これは、状態入力 `s` に対して、`m(s)` がその状態での予測または `num_actions` > 1 の場合は各アクションの予測のリストを返すことを意味します。同様に、`m(s,a)` は状態 `s` におけるアクション `a` の値を予測します。TabularModel は、`params`、`value_withgrad` など、TileCodingModel のすべての機能も継承します。

参照: [`TileCodingModel`](@ref), [`LinearModel`](@ref)
