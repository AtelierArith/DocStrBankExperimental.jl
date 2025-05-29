```
reverse_collatz_function(n; P=2, a=3, b=1)
```

コラッツ風の逆関数を1回適用した結果を返します。

# 引数

  * `n::Integer`: 逆コラッツ関数を適用する値

# キーワード引数

  * `P::Integer=2`: nを割るために使用されるモジュラス、nが(0 mod P)に等しい場合。
  * `a::Integer=3`: nを掛けるための係数。
  * `b::Integer=1`: nのスケーリングされた値に加える値。

# 例

```jldoctest
julia> print(reverse_collatz_function(1))
[2]
```

```jldoctest
julia> print(reverse_collatz_function(4))
[1, 8]
```

```jldoctest
julia> print(reverse_collatz_function(3, P=-3, a=-2, b=-5))
[-9, -4]
```
