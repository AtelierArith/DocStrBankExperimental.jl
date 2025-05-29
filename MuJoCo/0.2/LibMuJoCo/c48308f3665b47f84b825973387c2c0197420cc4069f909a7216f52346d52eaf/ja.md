```
mj_freeStack(d)
```

現在の mjData スタックフレームを解放します。mj*markStack への最後の呼び出し以降に mj*stackAlloc によって返されたすべてのポインタは、その後使用してはなりません。
