```
tridiagonal_solver(a, b, c, d)
```

三重対角ソルバー

# 説明

Gordon Bonanの元のコードからRコードに変換されました: Bonan, G. (2019). Climate Change and Terrestrial Ecosystem Modeling. Cambridge: Cambridge University Press. doi:10.1017/9781107339217

Uを求めるために、R * U = Dという方程式のセットを解きます。ここで、Uは長さNのベクトル、Dは長さNのベクトル、Rは長さNのベクトルA、B、Cによって定義されるN x Nの三重対角行列です。A(1)とC(N)は未定義であり、参照されません。

```
|B(1) C(1) ...  ...  ...                     |
|A(2) B(2) C(2) ...  ...                     |
```

R = |     A(3) B(3) C(3) ...                     |     |                    ... A(N-1) B(N-1) C(N-1)|     |                    ... ...    A(N)   B(N)  |

方程式の系は次のように書かれます:

A*i * U*i-1 + B*i * U*i + C*i * U*i+1 = D_i

i = 1からNまで。解は方程式を書き換えることによって見つけられます:

U*i = F*i - E*i * U*i+1

# 戻り値

  * `解: U`
