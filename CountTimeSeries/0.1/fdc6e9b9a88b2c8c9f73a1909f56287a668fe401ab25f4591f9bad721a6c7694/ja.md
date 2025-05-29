```
pit(results, nbins, level)
```

非ランダム化PITヒストグラムを計算する関数、詳細は[Czado et al.](https://mediatum.ub.tum.de/doc/1072660/1072660.pdf)を参照してください。

  * `results`: 推定結果
  * `nbins`: ビンの数（オプション、デフォルト = 10）
  * `level`: 信頼水準（オプション）

# 例

```julia-repl
pit(res, 10, 0.95)
```

引数`level`が指定されると、PITヒストグラムに信頼区間が追加されます。PIT値が一様分布に従う場合、すべてのビンの高さはその領域内に収まります。
