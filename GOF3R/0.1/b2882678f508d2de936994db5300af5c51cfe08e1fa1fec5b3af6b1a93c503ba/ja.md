```
s3stream(f, bucket, path)
```

`f(s3stream(bucket, path))`を呼び出し、`f`の実行が終了した後、エラーが発生した場合も含めてストリームが適切に閉じられることを確認します。
