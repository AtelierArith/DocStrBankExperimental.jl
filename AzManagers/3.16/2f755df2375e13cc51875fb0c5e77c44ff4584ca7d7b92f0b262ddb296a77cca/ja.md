```
ispreempted,notbefore = preempted([id=myid()|id="instanceid"])
```

マシン `id::Int` が Azure スポットプリエンプトメッセージを受信したかどうかを確認します。プリエンプトメッセージが受信された場合は (true, notbefore) を返し、そうでない場合は (false,"") を返します。`notbefore` は、マシンがまだ存在することが保証されている日時です。
