```
GrumpsThreads(; 
    blas = 0, 
    markets = 0, 
    inner = 0 
    )
```

これは、いくつかの注意事項に従って使用されるスレッドの数を設定します。 *blas* は BLAS スレッドの数を、*markets* は市場に対するループ内のスレッドの数を、*inner* は内部ループ内のスレッドの数を指します。 ゼロの値は、スレッドの数の自動選択を強制します。

これらの中で、*inner* は現在全く使用されておらず、*market* は *memsave* モードでのみ使用され、*blas* は使用されています。 ただし、Grumps が全体で使用するスレッドの数は、コマンドライン引数（すなわち -t スイッチを介して）で渡されたスレッドの数であり、その数には設定された BLAS スレッドの数は含まれませんのでご注意ください。
