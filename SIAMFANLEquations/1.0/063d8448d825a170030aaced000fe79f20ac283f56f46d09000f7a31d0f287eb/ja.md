```julia
function ptcsoli( F!, x0, FS, FPS, Jvec = dirder; rtol = 1.e-6, atol = 1.e-12,     maxit = 20, lmaxit = -1, lsolver = "gmres", eta = 0.1, fixedeta = true,     Pvec = nothing, PvecKnowsdelta = false, pside = "right", delta0 = 1.e-6,     dx = 1.e-7, pdata = nothing, printerr = true, keepsolhist = false, )

C. T. Kelley, 2022

Julia の SIAM 書籍からの非線形ソルバーのバージョン。 この本の新機能 ==> ptcsoli

PTC は u' = -F(u), u(0) = u_0 の定常状態解を見つけます。 - 記号は慣例です。

関数と Krylov 基底のストレージを事前に割り当てる必要があります –> 呼び出しプログラム内 <– つまり、FS と FPS で

入力:

  * F!: 関数評価、! は F! が FS を上書きすることを示します。これは、関数のために事前に割り当てたストレージです。

    したがって、FS=F!(FS,x) または FS=F!(FS,x,pdata) は FS=F(x) を返します。

    あなたの関数は必ず –> FS を返す <– 必要があります。 TestProblems/Systems/FBeam!.jl の例を参照してください。
  * x0: 初期反復値

  * FS: 関数のための事前に割り当てられたストレージ。サイズ N のベクトルです。

    (N) として保存し、F! をサイズ (N) のベクトルを使用するように設計する必要があります。代わりに (N,1) を一貫して使用すると、ソルバーは動作するかもしれませんが、保証はしません。
  * FPS: Krylov 基底のための事前に割り当てられたストレージ。これは N x m 行列で、再起動の前に最大 m-1 の GMRES 反復を行う予定です。

  * Jvec: ヤコビアンベクトル積。これを省略すると、デフォルトは有限差分方向微分です。

    したがって、FP=Jvec(v,FS,x) または FP=Jvec(v,FS,x,pdata) は FP=F'(x) v を返します。

    (v, FS, x) または (v, FS, x, pdata) が引数リストでなければなりません。たとえ FP が FS を必要としなくても。これの理由の一つは、有限差分微分が必要であり、それがソルバーのデフォルトだからです。
  * 精度: 精度についてお話ししましょう。このコードは、あなたが望む任意の精度で完全精度の関数と線形代数のために設計しました。FPS を Float64 または Float32 として宣言すると、ptcsoli は正しいことを行います。Float16 のサポートはありますが、うまく機能していません。

    ヤコビアンが適切に条件付けされている場合、直交化とストレージ (GMRES 用) のコストを半分に削減できますが、損失はありません。線形ソルバーが GMRES でない場合や、Krylov ベクトルの直交化とストレージが計算コストの小さな部分である場合は、利点はありません。したがって、前処理器が良好で、いくつかの Krylovs/Newton が必要な場合、精度を下げてもあまり役に立ちません。

    BiCGSTAB は精度を下げても利益を得ません。

---

キーワード引数 (kwargs):

rtol と atol: 相対および絶対誤差許容値

delta0: 初期擬似時間ステップ。デフォルト値の 1.e-3 は少し保守的で、実際に試すべきオプションの一つです。私が 1.0 に設定した例を見てください！

maxit: 非線形反復の制限、デフォルト=100。

これは delta0 に結びついています。delta0 の選択が小さすぎる (保守的) 場合、収束するために多くの反復が必要になり、maxit の値を大きくする必要があります。

PTC では、通常の非線形解法よりも多くの反復が必要です。これは安定した解を見つけるための代償の一部です。

lmaxit: 線形反復の制限。lmaxit > m-1 の場合、FPS に m 列があり、m-1 より多くの線形反復が必要な場合、GMRES は再起動します。

デフォルトは -1 です。GMRES の場合、これは m-1 の反復を行い、サイズ (V) = (n,m) で再起動なしで行います。BiCGSTAB の場合、デフォルトで 10 回の反復が行われます。

lsolver: 線形ソルバー、デフォルト = "gmres"

あなたの選択肢は "gmres" または "bicgstab" です。ただし、現時点では gmres のみがオプションです。

eta と fixed eta: eta > 0 でなければエラーです。

線形ソルバーは ||F'(x)s + F(x) || <= etag || F(x) || のときに終了します。

ここで

etag = eta もし fixedeta=true

etag = Eisenstat-Walker が本に実装されている場合、fixedeta=false のとき

デフォルトは、変更される可能性がありますが、eta=.1、fixedeta=true です。

Pvec: 前処理器-ベクトル積。ルールは Jvec と似ています。したがって、Pv=Pvec(v,x) または Pv=Pvec(v,x,pdata) は P(x) v を返します。P(x) は前処理器です。前処理器が x に依存しない場合でも、x を入力として使用する必要があります。

PvecKnowsdelta: 擬似時間ステップ delta に依存する前処理器-ベクトル積を希望する場合、事前計算されたデータに配列 deltaval を入れてください。これを次のように初期化します。deltaval = zeros(1,) そして、kwarg PvecKnowsdelta = true を設定することで ptcsoli に知らせます。ptcsoli は、pdata.deltaval[1]=delta のすべての変更で deltaval の値を更新します。これにより、前処理器-ベクトル積がそれにアクセスできるようになります。

pside: pside に前処理器を適用、デフォルト = "right"。 "left" はお勧めしません。ptcsoli にとって "left" の問題は、特に反復の初期段階で未前処理の方程式に対する不正確なニュートン条件を満たさない可能性があり、誤った結果 (不安定な解または定常状態の誤った分岐) を引き起こすことです。この件については第3章を参照してください。

dx: デフォルト = 1.e-7

有限差分微分における差分増分 h=dx*norm(x)+1.e-8 

pdata:

関数、ヤコビアン-ベクトル、および前処理器-ベクトル積のための事前計算データ。関数/Jacobian 内のグローバル変数にデータを隠すよりも、これを使用した方がうまくいきます。

F!, Jvec、または Pvec のいずれかで pdata を使用する場合、すべての関数で使用する必要があります。関数/Jacobian のための事前計算データ。関数/Jacobian 内のグローバル変数にデータを隠すよりも、これを使用した方がうまくいきます。

printerr: デフォルト = true

ソルバーが失敗したときに役立つメッセージを印刷します。そのメッセージを抑制するには、printerr を false に設定します。

keepsolhist: デフォルト = false

これを true に設定すると、出力タプルに反復の履歴が得られます。これはスカラー方程式の場合はデフォルトでオンになっており、システムの場合はオフになっています。データが本当に大きくなる可能性があるため、データを使用する必要がある場合にのみオンにしてください。

出力:

名前付きタプル (solution, functionval, history, stats, idid,                errcode, solhist) で、

solution = 収束した結果 functionval = F(solution) history = 反復の残差ノルムのベクトル (||F(x)||) stats = (ifun, ijac, ikfail) の履歴の名前付きタプル、各反復での関数/ヤコビアン-ベクトル積/線形ソルバーの失敗の数。

有限差分微分のための関数値は、ヤコビアン-ベクトル積にカウントされないため、カウントしません。

線形ソルバーの失敗は非線形反復を失敗させる必要はありません。警告が表示されるだけです。

idid=true は反復が成功した場合、false はそうでない場合。

errcode = 0 は反復が成功した場合

```

```
= -1 は初期反復値が終了基準を満たす場合
= 10 は maxit 反復後に収束しない場合
```

```

solhist:

これが、keepsolhist=true に設定した場合の反復の全履歴です。

solhist は N x K の配列で、N は x の長さ、K は反復の数 + 1 です。したがって、スカラー方程式の場合、行ベクトルになります。

### ptcsol の例

#### バッキングビーム問題。

これを機能させるには TestProblems を使用する必要があります。前処理器は高次項のソルバーです。

```

jldoctest julia> using SIAMFANLEquations.TestProblems

julia> function PreCondBeam(v, x, bdata)           J = bdata.D2           ptv = J\v        end PreCondBeam (generic function with 1 method)

julia> n=63; maxit=1000; delta0 = 0.01; lambda = 20.0;

julia> # 事前計算データを設定

julia> bdata = beaminit(n, 0.0, lambda);

julia> x = bdata.x; u0 = x .* (1.0 .- x) .* (2.0 .- x); 

julia> u0 .*= exp.(-10.0 * u0); FS = copy(u0); FPJV=zeros(n,20);

julia> pout = ptcsoli( FBeam!, u0, FS, FPJV;         delta0 = delta0, pdata = bdata, eta = 1.e-2,         rtol = 1.e-10, maxit = maxit, Pvec = PreCondBeam);

julia> # そこに到達するまでにいくつかの反復が必要です。        length(pout.history) 25

julia> [pout.history[1:5] pout.history[21:25]] 5×2 Matrix{Float64}:  6.31230e+01  1.79574e+00  7.45927e+00  2.65956e-01  8.73595e+00  6.58220e-03  2.91937e+01  8.34114e-06  3.47970e+01  5.06847e-09

julia> # 非負の定常状態を得ます。 julia> maximum(pout.solution) 2.19086e+00

julia> # さて、線形ソルバーに BiCGSTAB を使用します

julia> FPJV=zeros(n);

julia> pout = ptcsoli( FBeam!, u0, FS, FPJV;         delta0 = delta0, pdata = bdata,        eta = 1.e-2, rtol = 1.e-10, maxit = maxit,         Pvec = PreCondBeam, lsolver="bicgstab");

julia> # GMRES と同じ回数の反復ですが、各反復は二倍のコスト

julia> # ヤコビアン-ベクトル積とストレージははるかに少ない

julia> length(pout.history) 25

julia> [pout.history[1:5] pout.history[21:25]] 5×2 Matrix{Float64}:  6.31230e+01  1.68032e+00  7.47081e+00  2.35073e-01  8.62095e+00  5.18260e-03  2.96495e+01  3.23803e-06

```

```
