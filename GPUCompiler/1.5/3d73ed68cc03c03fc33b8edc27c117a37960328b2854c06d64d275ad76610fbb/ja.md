```
compile(target::Symbol, job::CompilerJob)
```

`target`引数で指定された形式のいずれかに`job`をコンパイルします: `:julia`はJulia IR、`:llvm`はLLVM IR、`:asm`は機械コードです。
