```
Qd     = c2d(sys::StateSpace{Continuous}, Qc::Matrix, Ts;             opt=:o)
Qd, Rd = c2d(sys::StateSpace{Continuous}, Qc::Matrix, Rc::Matrix, Ts; opt=:o)
Qd     = c2d(sys::StateSpace{Discrete},   Qc::Matrix;                 opt=:o)
Qd, Rd = c2d(sys::StateSpace{Discrete},   Qc::Matrix, Rc::Matrix;     opt=:o)
```

与えられた離散時間システムに適合する連続時間の共分散またはLQRコスト行列をサンプリングします。

`opt = :o`（デフォルト）の場合、行列は共分散行列であると仮定されます。測定共分散`R`も提供できます。`opt = :c`の場合、行列はLQR問題のコスト行列であると仮定されます。

!!! note
    測定共分散（ここでは`Rc`と呼ばれる）は通常、離散時間で推定され、サンプルレートには依存しません。測定共分散の離散化は、連続時間コントローラが設計され、最も近い対応する離散時間コントローラが望ましい場合にのみ意味があります。


使用される方法は、以下の参考文献の定理5に基づいています。

Ref: "Discrete-time Solutions to the Continuous-time Differential Lyapunov Equation With Applications to Kalman Filtering",  Patrik Axelsson and Fredrik Gustafsson

**特異共分散行列について:** 共分散行列`Qc = diagm([0,σ²])`を持つ従来の二重積分器は、特別な考慮が必要です。これはランクが不足しており、2つの状態変数が存在するにもかかわらず、単一のランダム性の源があることを示しています。ノイズが区分的に定数であると仮定すると、`Qc`の入力行列（「コレスキー因子」）を使用できます。例えば、分散`σ²`のノイズは`N = [0, 1]`のように入り、ZoHを使用してサンプリングされ、`Nd = [Ts^2 / 2; Ts]`となり、共分散行列`σ² * Nd * Nd'`が得られます。ノイズが連続時間のホワイトノイズプロセスであると仮定すると、離散化された共分散行列はフルランクであり、`c2d(sys::StateSpace{Continuous}, Qc, Ts)`によって計算できます。一部のアプリケーションでは、この行列のランク1近似が好まれます。そのような状況では、この行列の良いランク1近似は`σ² * Nd * Nd' ./ Ts`によって得られます。これは、ランクが低く、サンプル間隔の選択に対して共分散ダイナミクスがほぼ不変であるという利点があります。ZoHの仮定がなされると、共分散行列はランク1ですが、共分散ダイナミクスはサンプル間隔の選択に対して不変ではありません。

# 例:

以下の例は、共鳴システムのための連続時間LQRコントローラを設計します。これはOrdinaryDiffEqを使用してシミュレーションされ、ODEインテグレータが連続時間LQRコストも統合できるようにします（コストは追加の状態変数として追加されます）。次に、システムとコスト行列の両方を離散化し、同じことをシミュレーションします。この方法でのLQRコントローラの離散化は、時々`lqrd`と呼ばれます。

```julia
using ControlSystemsBase, LinearAlgebra, OrdinaryDiffEq, Test
sysc = DemoSystems.resonant()
x0 = ones(sysc.nx)
Qc = [1 0.01; 0.01 2] # 状態のための連続時間コスト行列
Rc = I(1)             # 入力のための連続時間コスト行列

L = lqr(sysc, Qc, Rc)
dynamics = function (xc, p, t)
    x = xc[1:sysc.nx]
    u = -L*x
    dx = sysc.A*x + sysc.B*u
    dc = dot(x, Qc, x) + dot(u, Rc, u)
    return [dx; dc]
end
prob = ODEProblem(dynamics, [x0; 0], (0.0, 10.0))
sol = solve(prob, Tsit5(), reltol=1e-8, abstol=1e-8)
cc = sol.u[end][end] # 連続時間コスト

# 離散時間バージョン
Ts = 0.01 
sysd = c2d(sysc, Ts)
Qd, Rd = c2d(sysd, Qc, Rc, opt=:c)
Ld = lqr(sysd, Qd, Rd)
sold = lsim(sysd, (x, t) -> -Ld*x, 0:Ts:10, x0 = x0)
function cost(x, u, Q, R)
    dot(x, Q, x) + dot(u, R, u)
end
cd = cost(sold.x, sold.u, Qd, Rd) # 離散時間コスト
@test cc ≈ cd rtol=0.01           # これらは類似しているはずです
```
