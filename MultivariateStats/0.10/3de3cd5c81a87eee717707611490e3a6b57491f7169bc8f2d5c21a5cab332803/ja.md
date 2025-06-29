```
ridge(X, y, r; ...)
```

リッジ回帰問題を解きます。

ここで、$y$はベクトルまたは各列が応答ベクトルである行列のいずれかです。

引数 `r` は二次正則化行列 $Q$ を与え、以下のいずれかの形式で指定できます：

  * `r` が実数スカラーの場合、$Q$ は `r * eye(n)` と見なされ、ここで `n` は `a` の次元です。
  * `r` が実数ベクトルの場合、$Q$ は `diagm(r)` と見なされます。
  * `r` が実対称行列の場合、$Q$ は単に `r` と見なされます。

この関数は2つのキーワード引数を受け入れます：

  * `dims`: 入力観測が行として保存されているか（`1`）列として保存されているか（`2`）。（デフォルトは `1`）
  * `bias`: バイアス項 `b` を含めるかどうか。（デフォルトは `true`）

この関数は解 `a` を返します。特に、`y` がベクトル（行列）の場合、`a` もベクトル（行列）です。`bias` が true の場合、返される配列は `[a; b]` として拡張されます。
