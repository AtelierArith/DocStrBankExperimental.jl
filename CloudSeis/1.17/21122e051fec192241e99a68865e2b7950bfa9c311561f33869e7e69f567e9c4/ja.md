```
foldmap(io; all=false, nasync=2048, showprogress=false)
```

現在キャッシュされている範囲の foldmap を返します（`all=false` の場合）または、全データセットの foldmap を返します（`all=true` の場合）。`all=true` の場合、操作は範囲に対して非同期マップを使用して実行されます。このマップ内の非同期タスクの数は `nasync` によって制御されます。`showprogress=true` を使用すると、foldmap を読み込んでいる間にプログレスバーが表示されます。
