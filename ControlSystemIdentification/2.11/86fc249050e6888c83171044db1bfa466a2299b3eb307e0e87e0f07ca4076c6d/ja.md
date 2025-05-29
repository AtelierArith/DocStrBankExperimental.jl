```
sys, x0, res = newpem(
    d,
    nx;
    zeroD  = true,
    focus  = :prediction,
    h      = 1,
    stable = true,
    sys0   = subspaceid(d, nx; zeroD, focus, stable),
    metric = abs2,
    regularizer = (p, P) -> 0,
    output_nonlinearity = nothing,
    input_nonlinearity = nothing,
    nlp = nothing,
    optimizer = BFGS(
        linesearch = LineSearches.BackTracking(),
    ),
    autodiff = :forward,
    store_trace = true,
    show_trace  = true,
    show_every  = 50,
    iterations  = 10000,
    time_limit  = 100,
    x_tol       = 0,
    f_abstol    = 0,
    g_tol       = 1e-12,
    f_calls_limit = 0,
    g_calls_limit = 0,
    allow_f_increases = false,
)

予測誤差法（PEM）の新しい実装です。この実装は実験的なものであり、semverを尊重しない破壊的変更の対象となる可能性があります。

予測誤差法は反復的な勾配ベースの最適化問題であり、そのため信号のスケーリングに対して非常に敏感です。推定の前に `d` にスケーリングを行うことをお勧めします。例えば、対角行列で前後に乗算することによって、`d̃ = Dy*d*Du` を行い、得られたシステムに逆スケーリングを適用します。この場合、次のようになります。

```

math D*y y = G̃ D*u u ↔ y = D*y^{-1} G̃ D*u u

```

したがって `G = Dy \ G̃ * Du` であり、$ G̃ $ はスケーリングされた iddata のために推定されたプラントです。例：

```

julia Dy = Diagonal(1 ./ vec(std(d.y, dims=2))) # 分散を正規化 Du = Diagonal(1 ./ vec(std(d.u, dims=2))) # 分散を正規化 d̃ = Dy * d * Du

```

手動で提供された初期推定 `sys0` がある場合、これも適切にスケーリングされる必要があります。

# 引数:

  * `d`: [`iddata`](@ref)
  * `nx`: モデル次数
  * `zeroD`: ゼロの `D` 行列を強制
  * `stable`: true の場合、推定されたシステムの安定性は、`ϵ=1/100`（デフォルト）を使用して [`schur_stab`](@ref) による固有値反射によって強制されます。`stable` が実数値の場合、その値がデフォルトの `ϵ` の代わりに使用されます。
  * `sys0`: 初期推定。提供されていない場合は、[`subspaceid`](@ref) が初期推定として使用されます。
  * `focus`: `prediction` または `:simulation`。` :simulation` の場合、`K` 行列はゼロになります。
  * `h`: 予測誤差フィルタの予測ホライズン。`h` の大きな値は計算コストが高くなります。`h` が無限大に近づくと、問題は `focus = :simulation` のケースに近づきます。
  * `optimizer`: Optim の最適化手法の1つ
  * `autodiff`: 勾配を計算するために前方モードのADを使用するかどうか。` :forward`（デフォルト）は前方モードのAD、または `:finite` は有限差分です。
  * `metric`: 残差を測定するために使用されるメトリック。例えば、外れ値に対する耐性を高めるために `abs` を試してみてください。

残りの引数は `Optim.Options` に関連しています。

  * `regularizer`: 推定を正則化するために使用できるパラメータベクトルと対応する `PredictionStateSpace/StateSpace` システムの関数。
  * `output_nonlinearity`: 単一の時点で出力信号 `yₜ` に作用し、インプレースで修正する `(y::Vector, p)` の関数。詳細は以下を参照してください。`p` は最適化可能な推定パラメータのベクトルです。
  * `input_nonlinearity`: 入力信号 `u` 全体に一度に作用し、インプレースで修正する `(u::Matrix, p)` の関数。詳細は以下を参照してください。`p` は `output_nonlinearity` と共有される推定パラメータのベクトルです。
  * `nlp`: 非線形パラメータの初期推定ベクトル。`output_nonlinearity` が提供されている場合、オプションで提供できます。

# 非線形推定

ハンマースタイン-ウィーナー形式の非線形システム、すなわち静的入力非線形性と静的出力非線形性を持ち、その間に線形システムがあるシステムは、非線形性が知られている限り推定できます。手順は次のとおりです。

1. **既知の入力非線形性** がある場合、推定の前に入力信号 `u` に手動で入力非線形性を適用します。すなわち、非線形に変換された入力を [`iddata`](@ref) オブジェクト `d` に使用します。**入力非線形性に未知のパラメータがある場合**、`newpem` にキーワード引数 `input_nonlinearity` を使用して入力非線形性を関数として提供します。この関数は、全体の（行列）入力信号 `u` に作用し、インプレースで修正することが期待されます。
2. 出力非線形性が *可逆* である場合、上記と同様に推定の前に出力信号 `y` に逆を適用します。
3. 出力非線形性が *可逆でない* 場合、非線形出力変換を関数として提供し、`newpem` にキーワード引数 `output_nonlinearity` を使用します。この関数は、（ベクトル）出力信号 `y` に作用し、インプレースで修正することが期待されます。例：

```

julia function output_nonlinearity(y, p)     y[1] = y[1] + p[1]*y[1]^2       # 受信ベクトルがインプレースで修正される様子に注意     y[2] = abs(y[2]) end

```

注意してください、`y = f(y)` は `y` をインプレースで変更するのではなく、新しいベクトル `y` を作成し、それを変数 `y` に割り当てます。これはここで望むものではありません。

`input_nonlinearity` と `output_nonlinearity` の第二引数は、最適化可能なパラメータの（オプションの）ベクトルです。このオプションを使用するには、非線形パラメータの初期推定のベクトルを持つキーワード引数 `nlp` を `newpem` に渡します。非線形パラメータは出力と入力の非線形性の間で共有されます。すなわち、これら2つの関数は同じパラメータのベクトルを受け取ります。

この推定の結果は、非線形性を *持たない* 線形システムです。

# 例

以下は線形システムからデータをシミュレートし、モデルを推定します。非線形同定の例については、ドキュメントを参照してください。

```

using ControlSystemIdentification, ControlSystemsBase Plots G = DemoSystems.doylesat() T = 1000  # 時間ステップ数 Ts = 0.01 # サンプル時間 sys = c2d(G, Ts) nx = sys.nx nu = sys.nu ny = sys.ny x0 = zeros(nx) # 実際の初期状態 sim(sys, u, x0 = x0) = lsim(sys, u; x0)[1]

σy = 1e-1 # ノイズ共分散

u  = randn(nu, T) y  = sim(sys, u, x0) yn = y .+ σy .* randn.() # 測定ノイズを追加 d  = iddata(yn, u, Ts)

sysh, x0h, opt = ControlSystemIdentification.newpem(d, nx, show_every=10)

plot(     bodeplot([sys, sysh]),     predplot(sysh, d, x0h), # 推定された初期状態を予測に含める )

```

返されるモデルは `PredictionStateSpace` 型であり、システムモデルを持つ `sys` フィールド、ならびに共分散行列とカルマンフィルタのための推定カルマンゲインを含みます。

[`structured_pem`](@ref) および [`nonlinear_pem`](@ref) も参照してください。

# 拡張ヘルプ

この実装は、最適化の観点から有利であることが示されている三重対角行列のパラメータ化を使用しています。¹ 初期推定 `sys0` は自動的に特別な三重対角モーダル形式に変換されます。 [1]: Mckelvey, Tomas & Helmersson, Anders. (1997). State-space parametrizations of multivariable linear systems using tridiagonal matrix forms.

最適化に使用されるパラメータベクトルは次の形式を取ります。

```

julia p = [trivec(A); vec(B); vec(C); vec(D); vec(K); vec(x0)]

```

ここで `ControlSystemIdentification.trivec` は `A` の `-1,0,1` 対角をベクトル化します。`focus = :simulation` の場合、`K` は省略され、`zeroD = true` の場合、`D` は省略されます。
```
