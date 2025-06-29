```
arec(A, B, R, Q, S; scaling = 'B', pow2 = false, as = false, rtol::Real = nϵ, orth = false, nrm = 1) -> (X, EVALS, F, Z, scalinfo)
```

連続時間代数リカッティ方程式のエルミート/対称安定解（`as = false`の場合）または反安定解（`as = true`の場合）`X`を計算します。

```
 A'X + XA - (XB+S)R^(-1)(B'X+S') + Q = 0,
```

ここで、`R`と`Q`はエルミート/対称行列または均一スケーリング演算子であり、`R`は非特異です。スカラー値の`R`と`Q`は、適切なサイズの均一スケーリング演算子`R*I`および`Q*I`として解釈されます。`S`が指定されていない場合、`S = zeros(size(B))`に設定されます。シュル法が[1]で使用されます。

計算の精度を向上させるために、デフォルト設定`scaling = 'B'`が使用されている場合、行列`R`、`Q`および`S`のブロックスケーリングが実行されます。このスケーリングは、`norm(Q) > norm(B)^2/norm(R)`の場合にのみ実行されます。`scaling = 'G'`が選択された場合、一般的な固有値計算指向のスケーリングとブロックスケーリングが組み合わされます。`scaling = 'S'`オプションを使用すると、構造を保持するスケーリングを実行できます。`scaling = 'K'`の場合、対称行列の均衡に基づくスケーリングが適用され、基になるベクトルノルムはキーワード引数`nrm = p`を使用して指定できます。ここで、`p = 1`がデフォルト設定です。実験的な構造を保持するスケーリングは、`scaling = 'D'`または`scaling = 'T'`オプションを使用して実行できます。スケーリングは、`scaling = 'N'`の選択で無効にできます。`pow2 = true`の場合、スケーリング要素は最も近い2の累乗に強制されます（デフォルト：`pow2 = false`）。

デフォルトでは、1ノルムの逆条件数`rtol`の下限は`n*ϵ`であり、ここで`n`は`A`の次数で、`ϵ`は`A`の要素型の*マシンイプシロン*です。

`EVALS`は、`A-BF`の（安定または反安定）固有値を含むベクトルです。

`F`は安定または反安定ゲイン行列`F = R^(-1)(B'X+S')`です。

`Z = [U; V; W]`は、関連する安定/反安定のデフレート部分空間の基底であり、`X = Sx*(V/U)*Sxi`および`F = -Sr*(W/U)*Sxi`となります。ここで、`Sx`、`Sxi`、および`Sr`は、名前付きタプル`scalinfo`に含まれる対角スケーリング行列であり、それぞれ`scalinfo.Sx`、`scalinfo.Sxi`、`scalinfo.Sr`です。直交基底`Z`は、計算コストが増加しますが、`orth = true`を設定することで決定できます。

`参考文献:`

[1] Laub, A.J., A Schur Method for Solving Algebraic Riccati equations.     IEEE Trans. Auto. Contr., AC-24, pp. 913-921, 1979.

# 例

```jldoctest
julia> using LinearAlgebra

julia> A = [-6. -2. 1.; 5. 1. -1; -4. -2. -1.]
3×3 Array{Float64,2}:
 -6.0  -2.0   1.0
  5.0   1.0  -1.0
 -4.0  -2.0  -1.0

julia> B = [1. 2.; 2. 0.; 0. 1.]
3×2 Array{Float64,2}:
 1.0  2.0
 2.0  0.0
 0.0  1.0

julia> R = [1. 0.; 0. 5.]
2×2 Array{Float64,2}:
 1.0  0.0
 0.0  5.0

julia> X, CLSEIG, F = arec(A,B,R,2I);

julia> X
3×3 Array{Float64,2}:
  0.522588   0.303007  -0.327227
  0.303007   0.650895  -0.132608
 -0.327227  -0.132608   0.629825

julia> A'*X+X*A-X*B*inv(R)*B'*X+2I
3×3 Array{Float64,2}:
 -2.66454e-15  -1.55431e-15   8.88178e-16
 -1.55431e-15   2.22045e-15  -2.9976e-15
  9.99201e-16  -2.9976e-15    4.44089e-16

julia> CLSEIG
3-element Array{Complex{Float64},1}:
   -4.37703628399912 + 2.8107164873731247im
   -4.37703628399912 - 2.8107164873731247im
 -1.8663764577096091 + 0.0im

julia> eigvals(A-B*F)
3-element Array{Complex{Float64},1}:
  -4.377036283999118 - 2.8107164873731234im
  -4.377036283999118 + 2.8107164873731234im
 -1.8663764577096063 + 0.0im
```
