iLQG - 決定論的有限ホライズン最適制御問題を解く。

最小化 sum_i cost(x[:,i],u[:,i]) + cost(x[:,end]) s.t.  x[:,i+1] = f(x[:,i],u[:,i])

# 入力

`f, costfun, df`

1. ステップ:

`xnew = f(x,u,i)` はフォワードパス中に呼び出されます。ここで状態 x と制御 u はベクトルです: size(x)==(n,), size(u)==(m,)。時間インデックス `i` はスカラーです。

2. コスト:

`cost = costfun(x,u)` はフォワードパス中に呼び出され、軌道 `x,u` に沿った時間ステップごとのコストを計算します。

3. 微分:

`fx,fu,fxx,fxu,fuu,cx,cu,cxx,cxu,cuu = df(x,u)` は軌道に沿った微分を計算します。この場合 size(x)==(n, N) で、N は軌道の長さです。size(u)==(m, N)。時間インデックスは I=(1:N) です。次元は変数名に一致します。例えば size(fxu)==(n, n, m, N) です。コスト関数またはシステムが時間不変の場合、対応する微分の次元は時間次元を削除することで減少できます。

`x0` - 制御問題を解くための初期状態。列ベクトルである必要があります。事前にロールされた軌道が利用可能な場合、size(x0)==(n, N) を提供し、コストをそれに応じて設定できます。

`u0` - 初期制御シーケンス。サイズ(u0)==(m, N) の行列で、m は制御の次元、N は状態遷移の数です。

# 出力

`x` - アルゴリズムによって見つかった最適状態軌道。size(x)==(n, N)

`u` - 最適オープンループ制御シーケンス。size(u)==(m, N)

`traj_new` - フィードフォワード制御軌道とフィードバックゲインを含む新しい `GaussianPolicy` オブジェクト。これらのゲインは、シミュレートされた軌道の偏差を名目軌道 x から乗算します。詳細については `?GaussianPolicy` を参照してください。

`Vx` - コスト・トゥ・ゴーの勾配。size(Vx)==(n, N)

`Vxx` - コスト・トゥ・ゴーのヘッセ行列。size(Vxx)==(n, n N)

`cost` - 軌道に沿ったコスト。size(cost)==(1, N) コスト・トゥ・ゴーは V = fliplr(cumsum(fliplr(cost))) です。

`trace` - 様々な収束関連の値のトレース。各イテレーションに対して1行、traceの列は `[iter λ α g_norm Δcost z sum(cost) dλ]` です。詳細は以下を参照してください。

# キーワード引数

`lims`,           [],            制御制限

`α`,              logspace(0,-3,11), バックトラッキング係数

`tol_fun`,         1e-7,          縮小終了基準

`tol_grad`,        1e-4,          勾配終了基準

`max_iter`,        500,           最大イテレーション数

`λ`,         1,             λ の初期値

`dλ`,        1,             dλ の初期値

`λfactor`,   1.6,           λ スケーリング係数

`λmax`,      1e10,          λ の最大値

`λmin`,      1e-6,          この値未満では λ = 0

`regType`,        1,             正則化タイプ 1: q*uu+λ*I 2: V*xx+λ*I

`reduce_ratio_min`,           0,             最小受け入れ縮小比

`diff_fun`,         -,             ユーザー定義のサブスペース最適化のための微分

`plot`,           1,             0: なし  k>0: 毎 k イテレーション k<0: 毎 k イテレーション、微分ウィンドウ付き

`verbosity`,      2,             0: なし  1: 最終 2: イテレーション 3: イテレーション、詳細

`plot_fun`,         x->0,          ユーザー定義のグラフィックスコールバック

`cost`,           [],            事前にロールされた軌道の初期コスト

このコードは、`INPROCEEDINGS{author={Tassa, Y. and Mansard, N. and Todorov, E.}, booktitle={Robotics and Automation (ICRA), 2014 IEEE International Conference on}, title={Control-Limited Differential Dynamic Programming}, year={2014}, month={May}, doi={10.1109/ICRA.2014.6907001}}` の著者によって提供された MATLAB ライブラリのポートと拡張から成ります。
