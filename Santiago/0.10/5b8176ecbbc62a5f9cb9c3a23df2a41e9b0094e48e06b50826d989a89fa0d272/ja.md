# 各技術の技術適合性スコア (TAS) を計算する

```
appropriateness(technology_file::AbstractString, case_file::AbstractString)
```

## パラメータ

  * `technology_file`: 技術定義を含むjsonファイルの名前
  * `case_file`: ケース定義を含むjsonファイルの名前

## 値

2つの辞書。最初の辞書は各技術のTASを返し、2番目の辞書は各属性のスコアを別々に含みます。
