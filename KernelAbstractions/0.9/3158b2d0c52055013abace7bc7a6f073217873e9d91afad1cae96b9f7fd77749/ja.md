カーネルの型付きIRを取得する

# 例

```
@ka_code_typed kernel(args. ndrange=...)
@ka_code_typed kernel(args. ndrange=... workgroupsize=...)
@ka_code_typed optimize=false kernel(args. ndrange=...)
```

インタラクティブモード（Cthulhuを使用）を使用するには、次のように呼び出します。

```
@ka_code_typed interactive=true kernel(args. ndrange=...)
```

ndrangeが静的に定義されている場合、次のように呼び出すことができます。

```
@ka_code_typed kernel(args.)
```

静的または動的な宣言を持つCPUまたはCUDAカーネルで機能します。
