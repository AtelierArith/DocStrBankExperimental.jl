```
CostModel(submat, insertion, deletion)
CostModel(submat, insertion=, deletion=)
CostModel(match=, mismatch=, insertion=, deletion=)
```

コストモデル。

これは、置換行列（`submat`）、挿入コスト（`insertion`）、および削除コスト（`deletion`）からアライメントのためのコストモデルオブジェクトを作成します。挿入コストと削除コストの両方は非負である必要があることに注意してください。二項置換行列を作成するための省略形として、例えば `CostModel(match=0, mismatch=1, insertion=2, deletion=2)` のように記述できます。

## 例

```
using BioAlignments

# 置換行列とインデルコストからコストモデルを作成
cost = CostModel(ones(128, 128) - eye(128), insertion=.5, deletion=.5)

# 編集距離を最小化するためにグローバルアライメントを実行
pairalign(EditDistance(), "intension", "execution", cost)
```

参照: `SubstitutionMatrix`, `pairalign`, `AffineGapScoreModel`
