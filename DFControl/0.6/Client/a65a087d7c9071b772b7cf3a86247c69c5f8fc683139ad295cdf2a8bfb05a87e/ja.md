```
abort(job::Job)
```

スケジューラのキューからジョブを削除しようとします。最後に実行された計算が `Calculation{QE}` であった場合、正しい中止ファイルが書き込まれます。他のコードの場合、プロセスはスムーズではなく、再起動が保証されているわけではありません。
