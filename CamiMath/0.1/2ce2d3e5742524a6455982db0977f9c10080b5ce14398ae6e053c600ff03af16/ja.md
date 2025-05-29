```
harmonicNumber(n::Integer [, p=1 [; arr=false [, msg=true]]])
```

最初の $n$ 個の正の整数の逆数の $p^{th}$ 乗の合計、

$$
    H_{n,p}=\sum_{k=1}^{n}\frac{1}{k^p}.
$$

  * `arr` : 配列形式で出力
  * `msg` : 整数オーバーフロー保護 (IOP) - 有効化時の警告

#### 例:

```
julia> o = [harmonicNumber(n) for n=1:8]; println(o)
Rational{Int64}[1//1, 3//2, 11//6, 25//12, 137//60, 49//20, 363//140, 761//280]

julia> harmonicNumber(8; arr=true)
(1//1, 3//2, 11//6, 25//12, 137//60, 49//20, 363//140, 761//280)

julia> harmonicNumber(42)
12309312989335019//2844937529085600

julia> harmonicNumber(43)
IOP capture: harmonicNumber(43, 1) converted to Rational{BigInt}
532145396070491417//122332313750680800

julia> harmonicNumber(12) == harmonicNumber(12, 1)
true

julia> harmonicNumber(12, -3) == faulhaber_summation(12, 3)
true

julia> o = [harmonicNumber(i, 5) for i=1:4]; println(o)
Rational{Int64}[1//1, 33//32, 8051//7776, 257875//248832]

julia> o = harmonicNumber(4, 5; arr=true); println(o)
(1//1, 33//32, 8051//7776, 257875//248832)
```
