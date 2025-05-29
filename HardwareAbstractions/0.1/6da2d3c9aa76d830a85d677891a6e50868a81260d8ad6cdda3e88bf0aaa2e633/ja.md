```
finalize(P::AbstractProcess)
```

この関数は、制御または測定操作が実行された後に呼び出されます。`finalize`の呼び出し中に、外部通信などを最終化することができます。制御が行われる前に、関数[`initialize`](@ref)が呼び出されます。
