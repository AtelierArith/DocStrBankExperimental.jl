```
XPRS_VARSELECTION
```

分岐と境界: これは、各整数変数の推定値を計算するために使用される式を決定し、したがって、特定のノードで分岐するために選択される整数変数を決定します。(整数)

分岐するために選択される変数は、最大の推定値を持つものです。

デフォルト値: `-1`

値: -1 : 自動的に決定されます。 1 : '上'と'下'の擬似コストの最小値。 2 : '上'の擬似コストと'下'の擬似コストの合計。 3 : '上'と'下'の擬似コストの最大値に、'上'と'下'の擬似コストの最小値の2倍を加えたもの。 4 : '上'と'下'の擬似コストの最大値。 5 : '下'の擬似コスト。 6 : '上'の擬似コスト。 7 : 変数がどれだけ分数であるかに依存する重みを持つ'上'と'下'の擬似コストの加重組み合わせ。 8 : '上'と'下'の擬似コストの積。
