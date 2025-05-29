```
shmdt(ptr)
```

は、呼び出し元のアドレス空間からSystem V共有メモリセグメントを切り離します。引数 `ptr` は、以前の[`shmat`](@ref)呼び出しによって返されたポインタです。

関連項目: [`shmat`](@ref), [`shmget`](@ref).
