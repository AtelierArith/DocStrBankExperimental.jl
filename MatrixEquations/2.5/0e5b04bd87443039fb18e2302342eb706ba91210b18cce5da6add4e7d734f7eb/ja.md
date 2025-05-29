```
ared(A, B, R, Q, S; scaling = 'B', pow2 = false, as = false, rtol::Real = nϵ, nrm = 1) -> (X, EVALS, F, Z, scalinfo)
```

離散時間代数リカッティ方程式のエルミート/対称安定解（`as = false`の場合）または反安定解（`as = true`の場合）を計算します。

```
A'XA - X - (A'XB+S)(R+B'XB)^(-1)(B'XA+S') + Q = 0,
```

ここで、`R`と`Q`はエルミート/対称行列です。スカラー値の`R`と`Q`は、適切なサイズの一様スケーリング演算子`R*I`と`Q*I`として解釈されます。`S`が指定されていない場合、`S = zeros(size(B))`に設定されます。

計算の精度を向上させるために、行列`R,` `Q`および`S`のブロック指向スケーリングがデフォルト設定`scaling = 'B'`を使用して実行されます。このスケーリングは、`norm(Q) > norm(B)^2/norm(R)`の場合にのみ実行されます。`scaling = 'G'`が選択された場合、一般的な固有値計算指向のスケーリングとブロックスケーリングが組み合わされます。構造を保持する代替スケーリングは、オプション`scaling = 'S'`を使用して実行できます。対称行列の均衡に基づくスケーリングは、`scaling = 'K'`の場合に使用され、基礎となるベクトルノルムはキーワード引数`nrm = p`を使用して指定できます。ここで、`p = 1`がデフォルト設定です。実験的な構造保持スケーリングは、オプション`scaling = 'D'`、`scaling = 'R'`および`scaling = 'T'`を使用して実行できます。スケーリングは、選択`scaling = 'N'`で無効にできます。`pow2 = true`の場合、スケーリング要素は最も近い2の累乗に強制されます（デフォルト：`pow2 = false`）。

デフォルトでは、1ノルムの逆条件数`rtol`の下限は`n*ϵ`であり、ここで`n`は`A`の次数で、`ϵ`は`A`の要素型の*マシンエプシロン*です。

`EVALS`は、`A-BF`の（安定した）固有値を含むベクトルです。

`F`は安定化ゲイン行列`F = (R+B'XB)^(-1)(B'XA+S')`です。

`Z = [U; V; W]`は、関連する安定/反安定のデフレート部分空間の直交基底であり、`X = Sx*(V/U)*Sxi`および`F = -Sr*(W/U)*Sxi`となります。ここで、`Sx`、`Sxi`および`Sr`は、名前付きタプル`scalinfo`に含まれる対角スケーリング行列であり、それぞれ`scalinfo.Sx`、`scalinfo.Sxi`および`scalinfo.Sr`です。

`参考文献:`

[1] W.F. Arnold, III and A.J. Laub,     Generalized Eigenproblem Algorithms and Software for Algebraic Riccati Equations,     Proc. IEEE, 72:1746-1754, 1984.

# 例

```jldoctest
julia> using LinearAlgebra

julia> A = [ 0. 1.; 0. 0. ]
2×2 Array{Float64,2}:
 0.0  1.0
 0.0  0.0

julia> B = [ 0.; sqrt(2.) ]
2-element Array{Float64,1}:
 0.0
 1.4142135623730951

julia> R = 1.
1.0

julia> Q = [ 1. -1.; -1. 1. ]
2×2 Array{Float64,2}:
  1.0  -1.0
 -1.0   1.0

julia> X, CLSEIG, F = ared(A,B,R,Q);

julia> X
2×2 Array{Float64,2}:
  1.0  -1.0
 -1.0   1.5

julia> A'*X*A-X-A'*X*B*inv(R+B'*X*B)*B'*X*A+Q
2×2 Array{Float64,2}:
  0.0          -3.33067e-16
 -3.33067e-16   8.88178e-16

julia> CLSEIG
2-element Array{Complex{Float64},1}:
 0.4999999999999998 - 0.0im
               -0.0 - 0.0im

julia> eigvals(A-B*F)
2-element Array{Float64,1}:
 -2.7755575615628914e-16
  0.5
```
