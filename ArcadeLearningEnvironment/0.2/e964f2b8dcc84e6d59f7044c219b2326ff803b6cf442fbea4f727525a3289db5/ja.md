```
restoreState(ale_instance::ALEPtr, state::ALEStatePtr)
```

cloneState()の逆操作です。これは擬似乱数性を復元しないため、確率的制御設定でrestoreState()を繰り返し呼び出しても同じ結果にはなりません。

参照: [`restoreSystemState`](@ref)
