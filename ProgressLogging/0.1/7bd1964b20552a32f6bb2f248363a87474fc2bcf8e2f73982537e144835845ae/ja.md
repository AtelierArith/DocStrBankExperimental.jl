```
@progress [name="", threshold=0.005] for i = ..., j = ..., ...
@progress [name="", threshold=0.005] x = [... for i = ..., j = ..., ...]
```

指定されたループまたは配列内包表記に対して、`name`という名前の進捗メーターを表示します。更新頻度は`threshold`によって制限されます（デフォルトでは進捗の0.5%ごとに1回の更新）。
