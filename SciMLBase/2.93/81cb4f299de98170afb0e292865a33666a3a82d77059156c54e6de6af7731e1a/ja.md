```
terminate!(i::DEIntegrator[, retcode = :Terminated])
```

`tstops`を空にすることで、積分器を終了します。これは、イベントやコールバックで解法プロセスを即座に終了するために使用できます。オプションで、`retcode`を指定することもできます（参照: [Return Codes (RetCodes)](@ref retcodes)）。
