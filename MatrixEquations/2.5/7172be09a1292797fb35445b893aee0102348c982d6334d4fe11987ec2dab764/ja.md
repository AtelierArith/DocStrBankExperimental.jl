```
arec(A, B, G, R, Q, S; scaling = 'B', pow2 = false, as = false, rtol::Real = nϵ, orth = false, nrm = 1) -> (X, EVALS, F, Z, scalinfo)
```

連続時間代数リカッティ方程式のエルミート/対称安定解（`as = false`の場合）または反安定解（`as = true`の場合）を計算します。

```
 A'X + XA - XGX - (XB+S)R^(-1)(B'X+S') + Q = 0,
```

ここで、`G`、`R`、および`Q`はエルミート/対称行列または一様スケーリング演算子であり、`R`は非特異です。スカラー値の`G`、`R`、および`Q`は、適切なサイズの一様スケーリング演算子`G*I`、`R*I`、および`Q*I`として解釈されます。`S`が指定されていない場合、`S = zeros(size(B))`に設定されます。条件の良い`R`の場合、[1]のシュア法が使用されます。条件の悪い`R`の場合、または`orth = true`の場合は、[2]の一般化シュア法が使用されます。

計算の精度を高めるために、デフォルト設定`scaling = 'B'`を使用して行列`G`、`R`、`Q`、および`S`のブロック指向スケーリングが行われます。このスケーリングは、`norm(Q) > max(norm(G), norm(B)^2/norm(R))`の場合にのみ実行されます。`scaling = 'G'`が選択された場合、一般的な固有値計算指向のスケーリングとブロックスケーリングが組み合わされます。代替の構造を保持するスケーリングは、オプション`scaling = 'S'`を使用して実行できます。`scaling = 'K'`の場合、対称行列の平衡に基づくスケーリングが採用され、基礎となるベクトルノルムはキーワード引数`nrm = p`を使用して指定できます。ここで、`p = 1`がデフォルト設定です。`orth = true`の場合、2つの実験的スケーリング手順がオプション`scaling = 'D'`および`scaling = 'T'`を使用して有効化できます。スケーリングは、選択`scaling = 'N'`で無効にできます。

デフォルトでは、1ノルムの逆条件数`rtol`の下限は`n*ϵ`であり、ここで`n`は`A`の次数で、`ϵ`は`A`の要素型の*マシンイプシロン*です。

`EVALS`は、`A-BF-GX`の（安定または反安定）固有値を含むベクトルです。

`F`は安定または反安定ゲイン行列`F = R^(-1)(B'X+S')`です。

`Z = [U; V; W]`は、関連する安定/反安定のデフレート部分空間の基底であり、`X = Sx*(V/U)*Sxi`および`F = -Sr*(W/U)*Sxi`となります。ここで、`Sx`、`Sxi`、および`Sr`は、名前付きタプル`scalinfo`に含まれる対角スケーリング行列であり、それぞれ`scalinfo.Sx`、`scalinfo.Sxi`、`scalinfo.Sr`です。直交基底`Z`は、計算コストが増加しますが、`orth = true`を設定することで決定できます。

`参考文献:`

[1] Laub, A.J., A Schur Method for Solving Algebraic Riccati equations.     IEEE Trans. Auto. Contr., AC-24, pp. 913-921, 1979.

[2] W.F. Arnold, III and A.J. Laub,     Generalized Eigenproblem Algorithms and Software for Algebraic Riccati Equations,     Proc. IEEE, 72:1746-1754, 1984.
