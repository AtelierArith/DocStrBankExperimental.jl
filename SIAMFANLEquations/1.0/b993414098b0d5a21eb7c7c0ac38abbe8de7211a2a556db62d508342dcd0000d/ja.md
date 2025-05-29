kl*gmres(x0, b, atv, V, eta, ptv=nothing; kl*store=nothing;               orth = "cgs2", side="right", lmaxit=-1, pdata=nothing)

C. T. Kelley, 2022

Gmres線形ソルバー。前処理と再起動を処理します。これらのことには完全に無関心なgmres_baseを使用します。

要点は次のとおりです。

入力:

x0:  初期反復、これは通常非線形ソルバーの場合はゼロです。

b:  右辺（当たり前！）

atv:  前計算データpdtaに依存する行列-ベクトル積。私はあなたがほとんどまたはすべての時間pdataを使用することを期待していますので、これはオプションの引数ではありません（少なくとも今のところ）。もしあなたのmat-vecが単にA*vであるなら、Aが前計算データである関数を書く必要があります。atvのAPIは`av=atv(v,pdata)`です。

V:  Krylovベクトル用の事前割り当てされたn x K配列。私は初期正規化残差を列1に保存しますので、gmres*baseが失敗を返す前に最大K-1回の反復があります。kl*gmresは再起動を処理し、lmaxit > 0の場合はlmaxit GMRES反復に達するまで続けます。VをFloat32で割り当ててストレージを節約することができます。これを行うことによるCPU時間の利益は劇的ではありません。

eta:  ||b - Ax|| <= eta || b ||のときに終了します。

ptv:  前処理器-ベクトル積で、pdataも使用します。デフォルトはnothingで、これは全く前処理を行わないことを意味します。ptvのAPIはpx=ptv(x,pdata)です。

キーワード引数

kl*store:  gmresが必要とするベクトルのためのスペースを提供するオプションがあります（やらないでください！）。これにはx0とbのコピーが含まれ、私はそれを上書きせず、反復で使用するいくつかのベクトルが含まれます。もしあなたが線形ソルバーだけを行っているなら、PLEASE kl*gmresでこれらのベクトルを割り当てさせてください。ニュートンステップを計算するか、繰り返し解く場合は、これを行う方法は`kl_store=kstore(n,"gmres")`で、ここでnは未知数の数です。あなたが私の前にこれを行わない場合、私は初期化フェーズでこれを自分で呼び出します。

```
     これには非常に注意してください。kl_storeは初期反復を上書きしないように解を保存するために使用されます。これは、同じkl_storeを持つkl_gmresへの2回の呼び出しが最初の呼び出しからの解に影響を与えることを意味します。私に割り当てさせると、それはローカルスコープで行われ、害はありません。
```

pdata: 前計算データ。デフォルトはnothingですが、これは非線形方程式にはうまく機能しません。

orth: あなたの選択による賢明なデフォルト、古典的なGram-Schmidtを2回、または何か遅くて安定性の低いもの。古典的なもの（本当に悪い）または修正されたGram-Schmidtのいくつかのバリアントです。mgs2は私が古いmatlabコードで使用したものです。ひどくはないですが、素晴らしいとは言えません。

side: 左または右の前処理。デフォルトは「右」です。

lmaxit: 最大線形反復回数。デフォルトは-1で、これは最大線形反復回数がK-1であることを意味し、これは再起動なしでVが許可するすべてです。もしlmaxit > K-1であれば、反復はlmaxit反復を消費するか、成功裏に終了するまで再起動します。

他のパラメータは途中で。

出力:

名前付きタプル (sol, reshist, lits, idid)

ここで

sol= 最終結果 reshist = 残差ノルムの履歴 lits = 反復回数 idid = 反復の状態        true -> 収束した         false -> 収束に失敗した

### kl_gmresのドキュメントストリングからの例

これらの例では行列があり、次のように使用します。

```
function atv(x, A)
    return A * x
end
```

matvecを計算します。

#### 三次元問題。

CGSで2回直交化した場合のみ、正しい3回の反復で収束します。

```jldoctest
julia> function atv(x, A)
           return A * x
       end
atv (generic function with 1 method)

julia> A = [0.001 0 0; 0 0.0011 0; 0 0 1.e4];

julia> V = zeros(3, 10); b = [1.0; 1.0; 1.0]; x0 = zeros(3);

julia> gout = kl_gmres(x0, b, atv, V, 1.e-10; pdata = A);

julia> gout.reshist
4-element Array{Float64,1}:
 1.73205e+00
 1.41421e+00
 6.72673e-02
 1.97712e-34

julia> norm(b - A*gout.sol,Inf)
1.28536e-10
```

#### 積分方程。pdataには演算子のカーネルがあり、私たちは直接matvecを行います。前の例と同じです。グリッド情報を入れ、この人工的な例では解を前計算データに入れます。

```jldoctest
julia> function integop(u, pdata)
           K = pdata.K
           return u - K * u
       end
integop (generic function with 1 method)

julia> function integopinit(n)
           h = 1 / n
           X = collect(0.5*h:h:1.0-0.5*h)
           K = [ker(x, y) for x in X, y in X]
           K .*= h
           sol = [usol(x) for x in X]
           f = sol - K * sol
           pdata = (K = K, xe = sol, f = f)
           return pdata
       end
integopinit (generic function with 1 method)

julia> function usol(x)
           return exp.(x) .* log.(2.0 * x .+ 1.0)
       end
usol (generic function with 1 method)

julia> function ker(x, y)
           ker = 0.1 * sin(x + exp(y))
       end
ker (generic function with 1 method)

julia> n=100; pdata = integopinit(n); ue = pdata.xe; f=pdata.f;

julia> u0 = zeros(size(f)); V = zeros(n, 20); V32=zeros(Float32,n,20);

julia> gout = kl_gmres(u0, f, integop, V, 1.e-10; pdata = pdata);

julia> gout32 = kl_gmres(u0, f, integop, V32, 1.e-10; pdata = pdata);

julia> [norm(gout.sol-ue,Inf) norm(gout32.sol-ue,Inf)]
1×2 Array{Float64,2}:
 4.44089e-16  2.93700e-07

julia> [gout.reshist gout32.reshist]
4×2 Array{Float64,2}:
 1.48252e+01  1.48252e+01
 5.52337e-01  5.52337e-01
 1.77741e-03  1.77742e-03
 1.29876e-19  8.73568e-11
```
