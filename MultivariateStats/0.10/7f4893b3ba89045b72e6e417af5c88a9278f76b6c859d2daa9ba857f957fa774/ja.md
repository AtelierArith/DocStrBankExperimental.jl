```
cov_whitening(C, regcoef)
```

正則化された共分散に基づいてホワイトニング変換を導出します。これは `C + (eigmax(C) * regcoef) * eye(d)` として表されます。
