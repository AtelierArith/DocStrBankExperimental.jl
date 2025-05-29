```
fibonacci(n::Integer [; arr=false [, msg=true]])
```

整数の列、 $F_0,⋯\ F_{nmax}$、各要素は前の2つの合計である、

$$
    F_n = F_{n-1}+F_{n-2}.
$$

$$
F_1=1
$$

および $F_0=0$ です。

  * `arr` : 完全なパスカルの三角形を出力
  * `msg` : 整数オーバーフロー保護 (IOP) - 有効化時に警告

#### 例:

```
julia> fibonacci(92)
7540113804746346429

julia> fibonacci(93)
IOP capture: fibonaci(93) converted to BigInt
12200160415121876738

julia> o = fibonacci(10; arr=true); println(o)
[1, 1, 2, 3, 5, 8, 13, 21, 34, 55]
```
