```
size_aircraft(ac::aircraft; iter=35, initwgt=false, Ldebug=false,
    printiter=true, saveOD=false)
```

指定された `aircraft` インスタンスのサイズを設定します。実際の作業を行う `_size_aircraft!` 関数の軽いラッパーです。
