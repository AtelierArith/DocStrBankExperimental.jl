```
dearddf(X, Y, measure)
```

入力 `X`、出力 `Y`、および効率測定 `measure` に対するデータ包絡分析逆方向距離関数 (RDDF) モデルを計算します。

# 測定仕様:

  * `:ERG`: 拡張ラッセルグラフ (またはスラックベース測定 (SBM))。
  * `:MDDF`: 修正方向距離関数。

# 方向仕様:

修正方向距離関数の場合、方向 `Gx` と `Gy` は次のシンボルのいずれかになります。

  * `:Ones`: 1を使用。
  * `:Observed`: 観測値を使用。
  * `:Mean`: 列の平均を使用。

# オプション引数

  * `orient=:Graph`: グラフ指向 `:Graph`、入力指向 `:Input`、または出力指向モデル `:Output` のいずれかを選択します。
  * `rts=:CRS`: 定常規模の収益 `:CRS` または変動規模の収益 `:VRS` のいずれかを選択します。
  * `atol=1e-6`: DMUが効率的と見なされるための許容誤差。
  * `Xref=X`: ユニットが評価される基準となる入力のセットを特定します。
  * `Yref=Y`: ユニットが評価される基準となる出力のセットを特定します。
  * `names`: 意思決定単位の名前を含む文字列のベクター。
