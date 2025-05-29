```
plot_verification_results(::MaliciousServer, ::Terse, xdata, ydata, label)
```

マリシャスサーバーの検証結果をテレースモードで散布図として生成します。この関数は、図と軸を作成し、データをプロットし、凡例を追加し、図を返します。

# 引数

  * `::MaliciousServer`: `MaliciousServer`のインスタンス。
  * `::Terse`: `Terse`のインスタンス。
  * `xdata`: プロットのためのxデータの配列。
  * `ydata`: プロットのためのyデータの配列。
  * `label`: 凡例で使用される文字列。

# 戻り値

  * 生成されたプロットを含むFigureオブジェクト。
