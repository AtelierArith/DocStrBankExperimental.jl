```
b = bias(P::AbstractProcess)
```

プロセスの入力バイアスを返します。これは、非線形システムが線形化される周りの定数入力 u₀ など、入力に存在する他のバイアスかもしれません。`length(b) = num_inputs(P)`
