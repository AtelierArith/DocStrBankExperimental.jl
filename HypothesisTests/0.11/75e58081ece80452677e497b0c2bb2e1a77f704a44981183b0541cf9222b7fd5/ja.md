```
BrownForsytheTest(groups)
BrownForsytheTest(groups::AbstractVector{<:Real}...)
```

ブラウン–フォーサイス検定は、`groups` の分散の等しさに関する統計的検定です。

ブラウン–フォーサイス検定は、各グループ内のばらつきを計算するために平均統計の代わりに中央値を使用するレヴェン検定の修正です。

実装: [`pvalue`](@ref)

# 参考文献

  * Brown, Morton B.; Forsythe, Alan B., "分散の等しさに関するロバスト検定". アメリカ統計協会誌. 69: 364–367, 1974 doi:[10.1080/01621459.1974.10482955](https://doi.org/10.1080%2F01621459.1974.10482955).

# 外部リンク

  * [ブラウン–フォーサイス検定 - Wikipedia](https://en.wikipedia.org/wiki/Brown%E2%80%93Forsythe_test)

```
