```
時間割
```

時間割を表すための可変型。

# コンストラクタ

  * `Timetable(numperiods::Vector{Int}, subjectcounts::SubjectCounts, teachers::Vector{Teacher}, division::Division)`

# フィールド

  * `numperiods::Vector{Int}`: 各行の期間の数。
  * `subjectcounts::SubjectCounts`: 時間割において科目が発生する回数の合計。
  * `subjects::Vector{String}`: 時間割における科目。
  * `teachers::Vector{Teacher}`: 時間割における教師。
  * `subjectteachers::OrderedDict{String, Vector{Teacher}}`: 各科目を教える教師。
  * `teacher_strs::OrderedDict{String, Teacher}`: 教師の文字列表現をオブジェクトにマッピングしたもの。
  * `division::Division`: 時間割の区分。
  * `data::Vector{Vector{Period}}`: 期間のベクトルのベクトルとしての時間割データ。

# 注意事項

  * `numperiods`、`subjectcounts`、`teachers`、および `division` のフィールドのみが渡されます。残りは推測されます。
  * 同じコンストラクタを参照してください。
