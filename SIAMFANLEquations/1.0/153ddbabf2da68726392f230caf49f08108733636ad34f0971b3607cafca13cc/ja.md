kl*bicgstab( x0, b, atv, V, eta, ptv = nothing;       kl*store=nothing, side = "right", lmaxit = 10, pdata = nothing) 

C. T. Kelley, 2022

BiCGSTAB 線形ソルバー。前処理に対応しています。 bicgstab_base を使用し、それに気を取られません。

コードは動作し、必要なことを行いますが...

ユーザーインターフェースは不安定で、さらに悪いことに、非線形ソルバーはまだ接続されていません。

この動作の仕組みは次のとおりです。

入力:

x0:  初期反復値。これは通常、非線形ソルバーの場合はゼロです。

b:  右辺（当たり前！）

atv:  前計算データ pdta に依存する行列-ベクトル積。私はあなたがほとんどまたはすべての時間 pdata を使用することを期待していますので、これはオプション引数ではありません（少なくとも今のところ）。もしあなたの mat-vec が単に A*v であるなら、A が前計算データである関数を書く必要があります。atv の API は av=atv(v,pdata) です。

V:  ジャコビアン-ベクトル積を格納するためのベクトル。これは gmres の FPS が入る場所です。V が Float64 であると最適です。

eta:  終了は ||b - Ax|| <= eta || b || のときに発生します。

ptv:  前処理ベクトル積。これも pdata を使用します。デフォルトは何もないことで、全く前処理が行われません。ptv の API は px=ptv(x,pdat) で、kl_gmres と同様です。

キーワード引数

kl*store:  bicgstab が作業を行うために必要なベクトルのためのスペースを提供するオプションがあります。これらは上書きされず、反復中に使用するいくつかのベクトルです。線形ソルバーのみを行う場合、kl*bicgstab でこれらのベクトルを割り当てることに害はありません。事前に割り当てる方法は `kl_store=kstore(n,"bicgstab")` で、n は未知数の数です。あなたが私の前にそれを行わない場合、私は初期化フェーズでこれを自分で呼び出します。

side: 左または右の前処理。デフォルトは "right" です。

lmaxit:  最大線形反復回数。デフォルトは 10 です。

pdata:  前計算データ。デフォルトは何もないですが、非線形方程式にはうまく機能しません。

出力:

名前付きタプル (sol, reshist, lits, idid)

ここで

sol= 最終結果 reshist = 残差ノルムの履歴 lits = 反復回数 idid = 反復の状態        true -> 収束した        false -> 収束に失敗した

### kl_bicgstab のドキュメント文字列からの例

これらの例では行列があり、次のように使用します。

```
function atv(x, A)
    return A * x
end
```

行列ベクトル積を計算します。

#### 三次元問題。

4 回の反復で収束します（kl_gmres より悪い）。

```jldoctest
julia> function atv(x, A)
           return A * x
       end
atv (generic function with 1 method)

julia> A = [0.001 0 0; 0 0.0011 0; 0 0 1.e4];

julia> V = zeros(3); b = [1.0; 1.0; 1.0]; x0 = zeros(3);

julia> gout.reshist
5-element Vector{Any}:
 1.73205e+00
 1.41421e+00
 3.21642e-03
 3.20321e-03
 4.98049e-13

julia> norm(b - A*gout.sol,Inf)
3.68594e-13
```

#### 積分方程。pdata がオペレーターのカーネルを持ち、行列ベクトル積を直接行います。前の例と同様です。グリッド情報と、この人工的な例の解を前計算データに入れます。

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

julia> u0 = zeros(size(f)); V = zeros(size(f));

julia> gout.reshist
4-element Vector{Any}:
 1.48252e+01
 2.90538e-02
 2.07823e-07
 2.17107e-17

julia> norm(gout.sol-ue,Inf)
8.88178e-16
```
