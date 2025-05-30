```
describe(io, chains[;
         q = [0.025, 0.25, 0.5, 0.75, 0.975],
         etype = :bm,
         kwargs...])
```

チェーンのメタデータ、要約統計、および分位数を表示します。REPL出力を`stdout`にするには`describe(chains)`を使用するか、他のストリーム（例：ファイル出力）のために`io`を指定します。
