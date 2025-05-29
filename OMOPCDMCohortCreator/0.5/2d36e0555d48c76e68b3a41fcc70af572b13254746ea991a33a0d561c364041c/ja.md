function GetCohortSubjectEndDate(cohort*ids, subject*ids, conn; tab=cohort)

```
与えられたコホートIDとサブジェクトIDのリストから、それらの終了日を返します。

# 引数:

- `cohort_ids` - `cohort_id`のリスト; 各IDは`Float64`のサブタイプでなければなりません
    
- `subject_id` - `subject_id`のリスト; 各IDは`Float64`のサブタイプでなければなりません
    
- `conn` - DBInterfaceを使用したデータベース接続
    
# キーワード引数:
    
- `tab` - `cohort`テーブルを表す`SQLTable`; デフォルトは`cohort`
```

# 戻り値

  * `df::DataFrame` - `:cohort_definition_id`、`:subject_id`、および`:cohort_end_date`の列から構成される3列の`DataFrame`
