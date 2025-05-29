```
p = characteristic_polynomial(g_ol)
```

オープンループ伝達関数 `g_ol` に関連する特性多項式を決定します。

特性多項式は $1+g_{ol}(s)$ です。特性多項式の根は、閉ループシステムの有界入力に対する応答の特性を決定します。

# 引数

  * `g_ol::TransferFunction`: オープンループ伝達関数

# 戻り値

`Polynomial` 型の多項式

# 例

```jldoctest
g_ol = 4 / (s + 3) / (s + 2) / (s + 1)
characteristic_polynomial(g_ol)
# 出力
Polynomial(10.0 + 11.0*s + 6.0*s^2 + 1.0*s^3)
```
