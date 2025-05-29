```
free(p::PtrArray)
```

[`malloc`](@ref)によって割り当てられた[`PtrArray`](@ref)によって割り当てられたメモリを解放します。

この関数は`malloc`によって返された`PtrArray`に対してのみ安全に呼び出すことができ、`free`を呼び出した後に`PtrArray`に対して操作を行うことは安全ではありません。
