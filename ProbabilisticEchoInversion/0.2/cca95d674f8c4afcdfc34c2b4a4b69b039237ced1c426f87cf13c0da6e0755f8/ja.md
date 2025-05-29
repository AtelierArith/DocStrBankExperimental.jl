```
unstack_echogram(echo_df, xcol, ycol, fcol, svcol[, X, Y, F])
```

長形式の `DataFrame` を多周波音響データからエコーグラムを表す三次元 `DimArray` に変換します。この `DataFrame` には以下の列が含まれている必要があります：

1. x座標（例：沿航路距離または時間）
2. y座標（例：深さまたはトランスデューサからの距離）
3. 音響周波数、および
4. 音響平均体積後方散乱（線形またはデシベル単位で可）

これらの列の名前は、`unstack_echogram` に第二から第五の引数として渡されます。

  * `echo_df::DataFrame` : xおよびy座標、音響周波数、後方散乱の列を持つ長形式の `DataFrame`。
  * `xcol`, `ycol`, `fcol`, `svcol` : `echo_df` 内の列の名前（`Symbol` として）
  * `X`, `Y`, `F` : 結果の `DimArray` のx、y、および周波数軸に適用するオプションの `Dimensions`。
