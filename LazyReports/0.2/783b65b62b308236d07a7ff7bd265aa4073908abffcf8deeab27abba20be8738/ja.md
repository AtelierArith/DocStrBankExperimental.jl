```
lazyreport()
lazyreport(contents...)
lazyreport(contents...)
```

遅延レポートを生成します。例えば、データ処理レポートです。

[`lazyreport!(rpt, contents...)`](@ref) を使用して、レポートにさらにコンテンツを追加します。

例:

```julia
using LazyReports, StructArrays, IntervalSets, Plots

tbl = StructArray(
    col1 = rand(5), col2 = ClosedInterval.(rand(5), rand(5).+1),
    col3 = [rand(3) for i in 1:5], col4 = rand(Bool, 5),
    col5 = [:a, :b, :c, :d, :e], col6 = ["a", "b", "c", "d", "e"],
    col7 = [:(a[1]), :(a[2]), :(a[3]), :(a[4]), :(a[5])]
)

rpt = lazyreport(
    "# 新しいレポート",
    "表 1:", tbl
)
lazyreport!(rpt, "図 1:", stephist(randn(10^3)))
lazyreport!(rpt, "図 2:", histogram2d(randn(10^4), randn(10^4), format = :png))

show(stdout, MIME"text/plain"(), rpt)
show(stdout, MIME"text/html"(), rpt)
show(stdout, MIME"text/markdown"(), rpt)

write_lazyreport("report.txt", rpt)
write_lazyreport("report.html", rpt)
write_lazyreport("report.md", rpt)
```

# 実装

`lazyreport` を直接特殊化せず、代わりに低レベルの関数 [`LazyReports.pushcontent!`](@ref) を特殊化します。
