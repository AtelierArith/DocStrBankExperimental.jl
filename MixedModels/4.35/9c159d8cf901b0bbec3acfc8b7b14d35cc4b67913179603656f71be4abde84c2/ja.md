```
replicate(f::Function, n::Integer; progress=true)
```

`f()`への`n`回の呼び出しの値のベクトルを返します - 値が確率的であるシミュレーションで使用されます。

`progress`は進行状況バーが表示されるかどうかを制御します。進行状況バーは、非対話型（つまり、ログ記録）コンテキストでは自動的に無効になります。
