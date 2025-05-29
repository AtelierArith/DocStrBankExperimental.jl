```
@usingModiaPlot()
```

`using XXX`を実行します。ここで、`XXX`は`usePlotPackage(plotPackage)`でアクティブにされたPlotパッケージです。したがって、これは@usingPlotPackage（SignalTablesから、Modiaから再エクスポートされています）に似ています。

ただし、XXX = "SilentNoPlot"の場合には違いがあります：

  * @usingPlotPackage()は`using SignalTables.SilentNoPlot`を実行し、そのため`SignalTables`パッケージがあなたの環境に利用可能である必要があります。
  * @usingModiaPlot()は`using Modia.SignalTables.SilentNoPlot`を実行し、そのため`Modia`パッケージがあなたの環境に利用可能である必要があります。

したがって、Modiaを使用する際には`@usingModiaPlot()`を使用する方が良いです。
