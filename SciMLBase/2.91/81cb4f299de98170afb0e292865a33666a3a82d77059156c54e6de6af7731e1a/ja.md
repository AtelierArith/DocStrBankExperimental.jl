```
terminate!(i::DEIntegrator[, retcode = :Terminated])
```

積分器を `tstops` を空にすることで終了します。これは、イベントやコールバックで解法プロセスを即座に終了するために使用できます。オプションで、`retcode` を指定することもできます（参照: [Return Codes (RetCodes)](@ref retcodes)）。
