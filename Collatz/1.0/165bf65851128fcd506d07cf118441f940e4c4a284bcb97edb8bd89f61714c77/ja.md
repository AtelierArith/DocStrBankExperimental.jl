```
collatz_function(n; P=2, a=3, b=1)
```

コラッツ風関数の単一適用の出力を返します。

# 引数

  * `n::Integer`: コラッツ風関数を適用する値

# キーワード引数

  * `P::Integer=2`: nを割るために使用されるモジュラス、nが(0 mod P)に等しい場合。
  * `a::Integer=3`: nを掛けるための係数。
  * `b::Integer=1`: nのスケーリングされた値に加える値。

# 例

```jldoctest
julia> collatz_function(5)
16
```

```jldoctest
julia> collatz_function(14, P=7)
2
```

```jldoctest
julia> collatz_function(15, P=7, a=5, b=3)
78
```
