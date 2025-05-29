```
jacobi_symbol(x::Int, y::Int)
```

ジャコビ記号 $\left(\frac{x}{y}\right)$ の値を返します。モジュラス $y$ は奇数で正でなければならず、そうでない場合は `DomainError` がスローされます。
