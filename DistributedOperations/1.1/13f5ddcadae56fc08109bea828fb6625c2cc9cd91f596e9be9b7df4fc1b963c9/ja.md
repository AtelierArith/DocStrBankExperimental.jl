```
bcast!(x::TypeFutures, pids)
```

既存の `x::TypeFutures` を `pids` にブロードキャストします。これは、クラスターが `x::TypeFuture` の構築とブロードキャストの後に成長する可能性がある弾力的コンピューティングに役立ちます。
