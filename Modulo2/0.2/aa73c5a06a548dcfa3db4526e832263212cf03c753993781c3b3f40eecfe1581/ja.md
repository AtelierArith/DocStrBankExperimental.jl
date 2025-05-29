```
ZZ2 <: Number
```

2の剰余に関する整数を表す型です。

要素は、`zero`および`one`関数を介して、または`Bool`型や他の`Integer`型の引数から作成できます。より一般的には、`isodd`が受け入れる任意の引数は`ZZ2`に変換できます。`ZZ2`を用いた代数計算では、`Integer`型は`ZZ2`に昇格されます。逆に、`ZZ2`型の要素は`Bool`に変換できます。

関連情報として、`Base.zero`、`Base.one`、`Base.iszero`、`Base.isone`、`Base.isodd`を参照してください。

# 例

```jldoctest
julia> ZZ2(1) == one(ZZ2)
true

julia> iszero(ZZ2(4.0))
true

julia> x = ZZ2(1) + 3
0

julia> typeof(x)
ZZ2

julia> Bool(x), convert(Bool, x)
(false, false)
```
