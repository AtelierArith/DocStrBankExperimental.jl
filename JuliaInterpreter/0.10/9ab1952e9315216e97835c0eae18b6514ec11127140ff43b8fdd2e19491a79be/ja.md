```
@breakpoint f(args...) condition=nothing
@breakpoint f(args...) line condition=nothing
```

`f(args...)`によって呼び出されるメソッドにおいて、エントリ時または指定された行番号でブレークします。オプションで、引数やメソッドの内部変数に基づいて表現された条件を指定できます。`line`が指定されている場合、それはリテラル整数でなければなりません。

# 例

次のように`mysum`メソッドが定義されているとします。左側の数字はファイル内の行番号です。

```
12 function mysum(A)
13     s = zero(eltype(A))
14     for a in A
15         s += a
16     end
17     return s
18 end
```

この場合、

```
@breakpoint mysum(A) 15 s>10
```

は`s>10`のときにループの実行をブレークさせます。
