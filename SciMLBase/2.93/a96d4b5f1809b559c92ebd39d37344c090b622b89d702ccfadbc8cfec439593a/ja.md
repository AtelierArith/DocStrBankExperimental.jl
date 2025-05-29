```
set_proposed_dt!(i::DEIntegrator,dt)
set_proposed_dt!(i::DEIntegrator,i2::DEIntegrator)
```

次のタイムステップのための提案された `dt` を設定します。第二引数が `DEIntegrator` の場合、最初の引数のタイムステッピングを第二引数のものに合わせます。PI制御とステップ加速のため、これはほとんどの場合、単に因子を一致させる以上のものです。
