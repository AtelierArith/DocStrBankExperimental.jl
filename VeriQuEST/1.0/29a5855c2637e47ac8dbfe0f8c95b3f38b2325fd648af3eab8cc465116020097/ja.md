```
plot_verification_results(::MaliciousServer, ::Verbose, xdata, ydata, label)
```

マリシャスサーバーの検証結果を詳細モードでバー プロットとして生成します。この関数はyデータを正規化し、図と軸を作成し、データをプロットし、凡例を追加し、図を返します。

# 引数

  * `::MaliciousServer`: `MaliciousServer`のインスタンス。
  * `::Verbose`: `Verbose`のインスタンス。
  * `xdata`: プロットのxデータの配列。
  * `ydata`: プロットのyデータの配列。
  * `label`: 凡例に使用される文字列。

# 戻り値

  * 生成されたプロットを含むFigureオブジェクト。
