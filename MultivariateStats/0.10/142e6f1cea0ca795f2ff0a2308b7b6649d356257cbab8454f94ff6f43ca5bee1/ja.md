```
llsq(X, y; ...)
```

線形最小二乗問題を解きます。

ここで、`y`はベクトルまたは各列が応答ベクトルである行列のいずれかです。

この関数は2つのキーワード引数を受け入れます：

  * `dims`: 入力観測が行として保存されているか（`1`）列として保存されているか（`2`）。（デフォルトは`1`）
  * `bias`: バイアス項`b`を含めるかどうか。（デフォルトは`true`）

関数は解`a`を返します。特に、`y`がベクトル（行列）の場合、`a`もベクトル（行列）です。`bias`がtrueの場合、返される配列は`[a; b]`として拡張されます。
