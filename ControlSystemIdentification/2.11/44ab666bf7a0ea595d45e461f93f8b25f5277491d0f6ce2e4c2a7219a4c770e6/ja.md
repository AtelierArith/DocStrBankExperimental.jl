```
find_nanb(d::InputOutputData, na, nb; logrms = false, method = :aic)
```

モデル次数 `na`, `nb` までの RMSE と AIC をプロットします。モデル選択に役立ちます。`na` は整数または範囲のいずれかで指定できます。`nb` についても同様です。

  * `logrms`: RMS エラーの底 10 の対数をプロットするかどうかを決定します。
  * `method`: モデル次数を決定するために、赤池情報量基準 (`:aic`) または最終予測誤差 (`:fpe`) を使用するかどうかを決定します。

色スケールが非常に大きなエラーを表すタイルが少ないために読みづらい場合は、整数の代わりに `na` と `nb` の範囲を指定してタイルを描画しないようにします。例えば、`find_nanb(d, 3:na, 3:nb)` を使用してモデル次数が 2 未満のものを表示しないようにします。
