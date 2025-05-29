```
lqr(sys, Q, R)
lqr(Continuous, A, B, Q, R, args...; kwargs...)
lqr(Discrete, A, B, Q, R, args...; kwargs...)
```

コスト関数を最小化する状態フィードバック法 `u = -K*x` の最適ゲイン行列 `K` を計算します：

J = integral(x'Qx + u'Ru, 0, inf) 連続時間モデル `dx = Ax + Bu` の場合。 J = sum(x'Qx + u'Ru, 0, inf) 離散時間モデル `x[k+1] = Ax[k] + Bu[k]` の場合。

状態空間システム `sys` の LQR 問題を解決します。離散時間システムと連続時間システムの両方に対応しています。

`args...; kwargs...` はリカッティソルバーに送信され、クロス共分散などの指定が可能です。詳細については `?MatrixEquations.arec / ared` を参照してください。

リカッティ方程式の解と閉ループシステムの固有値も取得するには、代わりに `ControlSystemsBase.MatrixEquations.arec / ared` を呼び出してください（これらの関数への引数の順序が異なることに注意してください）。

連続時間 LQR 問題の離散時間近似を取得するには、関数 [`c2d`](@ref) を使用して対応する離散時間コスト行列を取得できます。

# 例

連続時間

```julia
using LinearAlgebra # 単位行列 I のため
using Plots
A = [0 1; 0 0]
B = [0; 1]
C = [1 0]
sys = ss(A,B,C,0)
Q = I
R = I
L = lqr(sys,Q,R) # lqr(Continuous,A,B,Q,R) も使用できます

u(x,t) = -L*x # 制御法則を形成する、
t=0:0.1:5
x0 = [1,0]
y, t, x, uout = lsim(sys,u,t,x0=x0)
plot(t,x', lab=["位置" "速度"], xlabel="時間 [s]")
```

離散時間

```julia
using LinearAlgebra # 単位行列 I のため
using Plots
Ts = 0.1
A = [1 Ts; 0 1]
B = [0;1]
C = [1 0]
sys = ss(A, B, C, 0, Ts)
Q = I
R = I
L = lqr(Discrete, A,B,Q,R) # lqr(sys,Q,R) も使用できます

u(x,t) = -L*x # 制御法則を形成する、
t=0:Ts:5
x0 = [1,0]
y, t, x, uout = lsim(sys,u,t,x0=x0)
plot(t,x', lab=["位置"  "速度"], xlabel="時間 [s]")
```

# FAQ

この関数には以下が必要です

  * `Q` は正半定値でなければならない
  * `R` は正定値でなければならない
  * ペア `(Q,A)` は虚軸（連続）/ 単位円（離散）上に観測不可能なモードを持ってはいけません。例えば、`Q` によってペナルティが課されていない積分モードがあってはいけません。この条件が満たされない場合、「ハミルトニアン行列は二分されていません」というエラーが発生する可能性があります。

```
