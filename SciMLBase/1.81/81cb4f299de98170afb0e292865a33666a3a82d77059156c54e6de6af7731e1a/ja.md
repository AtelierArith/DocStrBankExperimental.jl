```
terminate!(i::DEIntegrator[, retcode = :Terminated])
```

積分器を `tstops` を空にすることで終了します。これは、イベントやコールバックで解決プロセスを即座に終了するために使用できます。オプションで、`retcode` を指定することができます（参照: [Return Codes (RetCodes)](@ref retcodes)）。
