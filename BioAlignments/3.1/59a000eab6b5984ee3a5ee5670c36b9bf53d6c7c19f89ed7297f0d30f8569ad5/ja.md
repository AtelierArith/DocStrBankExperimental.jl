```
AffineGapScoreModel(submat, gap_open, gap_extend)
AffineGapScoreModel(submat, gap_open=, gap_extend=)
AffineGapScoreModel(match=, mismatch=, gap_open=, gap_extend=)
```

アフィンギャップスコアモデル。

これは、置換行列（`submat`）、ギャップオープニングスコア（`gap_open`）、およびギャップ拡張スコア（`gap_extend`）からアライメントのためのアフィンギャップスコアリングモデルオブジェクトを作成します。長さ `k` の連続したギャップのスコアは `gap_open + gap_extend * k` です。両方のギャップスコアは非正である必要があります。二項置換行列を作成するための省略形として、例えば `AffineGapScoreModel(match=5, mismatch=-3, gap_open=-2, gap_extend=-1)` と書くことができます。

## 例

```
using BioSequences
using BioAlignments

# 事前定義された置換行列とギャップオープニング/拡張スコアから
# アフィンギャップスコアリングモデルを作成します。
affinegap = AffineGapScoreModel(BLOSUM62, gap_open=-10, gap_extend=-1)

# 2つのアミノ酸配列間でグローバルアライメントを実行します
pairalign(GlobalAlignment(), aa"IDGAAGQQL", aa"IDGATGQL", affinegap)
```

参照: `SubstitutionMatrix`, `pairalign`, `CostModel`
