```
quick_reg(
    data::FixedTable,
    f::FormulaTerm;
    minobs::Real=0.8,
    save_residuals::Bool=false
)

quick_reg(
    data::IterateFixedTable,
    f::FormulaTerm;
    minobs::Real=0.8,
    save_residuals::Bool=false
)
```

提供されたデータに基づいて、式（StatsModels.jlからの式）に基づいて線形回帰を計算します。式が明示的に切片を除外しない限り（すなわち、`@formula(y ~ 0 + x)`）、切片が追加されます。

`data`が`IterateFixedTable`型の場合、関数は各`FixedTable`で最大数のスレッドを最適な方法で使用し、`Vector{BasicReg}`を返します。

## 引数

  * `minobs::Real`: 完全な回帰を返すための最小観測数。1未満の場合、その値は期間内の営業日数に対する割合として使用されます。したがって、デフォルトの0.8は、期間内の営業日の少なくとも80％に値があることに対応します。
  * `save_residuals::Bool=false`: 残差を`BasicReg`に保存するかどうか。このことはパフォーマンスに大きな影響を与える可能性があります。
