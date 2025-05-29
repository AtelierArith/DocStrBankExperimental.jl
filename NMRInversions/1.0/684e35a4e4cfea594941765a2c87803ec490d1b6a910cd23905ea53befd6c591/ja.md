```
mexp(seq, u, x)
```

パラメータ `u` から多重指数関数を構築し、値 `x` で評価します。

`u` ベクトルは [a1, b1, a2, b2, ...] の形式である必要があり、ここで a は振幅、b は減衰定数の逆数です。`u` の長さは偶数でなければなりません。

例:

mexp(CPMG, [a,b] , x) = a * exp.( (1/b) * x) 

mexp(CPMG, [a,b,c,d] , x) = a * exp.( (1/b) * x) + c * exp.((1/d) * x) 

mexp(CPMG, [a,b,c,d,e,f] , x) = a * exp.( (1/b) * x) + c * exp.((1/d) * x) + e * exp.((1/f) * x) 

（ここで a,b,c,d,e,f はすべて数値です） . . .
