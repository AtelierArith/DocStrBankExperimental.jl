```
exog_endo!(plan, exog_vars, endo_vars, date)
```

与えられた計画を修正して、`exog_vars` にリストされた変数が外生的であり、`endo_vars` にリストされた変数が与えられた日付で内生的になるようにします。`exog_vars` と `endo_vars` はそれぞれ `Symbol` または `String` またはそのようなものの `Vector` であることができます。`date` は時間の瞬間（計画と同じタイプ）、または範囲、または反復可能なもの、またはコンテナであることができます。
