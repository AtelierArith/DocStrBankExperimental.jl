```
@uninterpreted(f, Int, Bool) # fはIntExprを入力として受け取り、BoolExprを返します
@uninterpreted(g, (BitVector, 32), (BitVector, 32)) # gの入力と出力の値は長さ32のBitVectorです

SMT-LIBの非解釈関数を定義します。非解釈関数は、入力値と出力値の間の未知のマッピングと考えることができます。SMTソルバーのタスクは、あるブール文が真であるようなマッピングが存在するかどうかを判断することです。

例えば、`f(x)`が存在して`f(f(x)) == x`、`f(x) == y`、`x != y`が成り立つかどうかを尋ねることができます。

```

julia @satvariable(x, Bool) @satvariable(y, Bool) @uninterpreted(f, Bool, Bool)

status = sat!(distinct(x,y), f(x) == y, f(f(x)) == x, solver=Z3()) println("status = :status") ```
