カーネルのLLVMコードを取得する

# 例

```
@ka_code_llvm kernel(args. ndrange=...)
@ka_code_llvm kernel(args. ndrange=... workgroupsize=...)
@ka_code_llvm optimize=false kernel(args. ndrange=...)
```

ndrangeが静的に定義されている場合、次のように呼び出すことができます。

```
@ka_code_llvm kernel(args.)
```

静的または動的宣言を持つCPUカーネルのみに対応しています。
