```
aws_autogen_style
```

[`aws_input_stream`](@ref) テスターを使用して、入力ストリームを受け取るシステムのエッジケースをテストします。特定の奇妙な方法で動作させることができます（例：3回目の読み取りで失敗する）。

ストリームされる内容を設定する方法はいくつかあります。 - source*bytes: 設定されている場合、これらのバイトをストリームします。 - source*stream: 設定されている場合、このストリームをラップします（ただし、3回目の読み取りで失敗するなどの奇妙な動作を挿入します）。 - autogen_length: 自動生成されたストリーミングコンテンツの長さNバイト。
