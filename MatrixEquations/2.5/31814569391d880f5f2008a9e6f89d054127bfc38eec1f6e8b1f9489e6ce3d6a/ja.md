```
garec(A, E, B, G, R, Q, S; scaling = 'B', pw2 = false, as = false, rtol::Real = nϵ, nrm = 1) -> (X, EVALS, F, Z, scalinfo)
```

一般化連続時間代数リカッティ方程式のヘルミート/対称安定解（`as = false`の場合）または反安定解（`as = true`の場合）である`X`を計算します。

```
A'XE + E'XA - E'XGXE - (E'XB+S)R^(-1)(B'XE+S') + Q = 0,
```

ここで、`G`、`Q`、および`R`はヘルミート/対称行列であり、`R`は非特異で、`E`は非特異行列です。スカラー値の`G`、`R`、および`Q`は、適切なサイズの一様スケーリング演算子`G*I`、`R*I`、および`Q*I`として解釈されます。一般化シュル法が[1]を使用して適用されます。

計算の精度を向上させるために、デフォルト設定`scaling = 'B'`を使用して行列`G`、`R`、`Q`、および`S`のブロック指向スケーリングが実行されます。このスケーリングは、`norm(Q) > max(norm(G), norm(B)^2/norm(R))`の場合にのみ実行されます。`scaling = 'G'`が選択された場合、一般的な固有値計算指向のスケーリングとブロックスケーリングが組み合わされます。オプション`scaling = 'S'`を使用すると、構造を保持する代替スケーリングが実行できます。`scaling = 'K'`の場合、対称行列の均衡に基づくスケーリングが適用され、基礎となるベクトルノルムはキーワード引数`nrm = p`を使用して指定できます。ここで、`p = 1`がデフォルト設定です。実験的な構造保持スケーリングは、オプション`scaling = 'D'`または`scaling = 'T'`を使用して実行できます。スケーリングは、選択`scaling = 'N'`で無効にできます。`pow2 = true`の場合、スケーリング要素は最も近い2の累乗に強制されます（デフォルト：`pow2 = false`）。

デフォルトでは、1ノルムの逆条件数の下限`rtol`は`n*ϵ`であり、ここで`n`は`A`の次数で、`ϵ`は`A`の要素型の*マシンエプシロン*です。

`EVALS`は、ペア`(A-BF-GXE,E)`の（安定または反安定）一般化固有値を含むベクトルです。

`F`は安定/反安定ゲイン行列`F = R^(-1)(B'XE+S')`です。

`Z = [U; V; W]`は、関連する安定/反安定のデフレート部分空間の直交基底であり、`X = (Sx*(V/U)*Sxi)/E`および`F = -Sr*(W/U)*Sxi`となります。ここで、`Sx`、`Sxi`、および`Sr`は、名前付きタプル`scalinfo`に含まれる対角スケーリング行列であり、それぞれ`scalinfo.Sx`、`scalinfo.Sxi`、`scalinfo.Sr`として表されます。

`参考文献:`

[1] W.F. Arnold, III and A.J. Laub,     Generalized Eigenproblem Algorithms and Software for Algebraic Riccati Equations,     Proc. IEEE, 72:1746-1754, 1984. ```
