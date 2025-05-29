```
bigfactorial(n::Int [; msg=true])
```

`n`以下のすべての*正*整数の積、

$$
n!=n(n-1)(n-2)⋯1.
$$

さらに、$0!=1$は定義によるものです。*負*の整数に対しては階乗はゼロです。

  * `msg` : 整数オーバーフロー保護 (IOP) - 有効化時の警告 (n > 20 の場合)

#### 例:

```
julia> bigfactorial(20) == factorial(20)
true

julia> bigfactorial(21)
IOP capture: bigfactorial(21) converted to BigInt
51090942171709440000

julia> bigfactorial(21; msg=false)
51090942171709440000

julia> factorial(21)
ERROR: OverflowError: 21 is too large to look up in the table; consider using 
`factorial(big(21))` instead
```
