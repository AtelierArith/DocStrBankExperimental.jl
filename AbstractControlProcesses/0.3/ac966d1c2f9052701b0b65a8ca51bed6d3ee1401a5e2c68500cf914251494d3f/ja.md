```
initialize(P::AbstractProcess)
```

この関数は、制御または測定操作が実行される前に呼び出されます。`initialize`の呼び出し中に、外部通信などを設定することができます。制御が完了した後、関数[`finalize`](@ref)が呼び出されます。
