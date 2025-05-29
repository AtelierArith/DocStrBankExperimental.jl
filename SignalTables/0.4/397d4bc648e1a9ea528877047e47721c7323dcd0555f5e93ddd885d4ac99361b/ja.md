```
writeSignalTable(filename::String, signalTable; signalNames=nothing, indent=nothing, log=false)
```

`filename`にJSON形式でsignalTableを書き込みます。

キーワードsignalNamesに文字列のベクターが指定されている場合、対応する信号を持つ信号テーブルがファイルに保存されます。

indent=<number>が指定されている場合、<number>のインデントが使用されます（そうでない場合は、コンパクトな表現になります）。
