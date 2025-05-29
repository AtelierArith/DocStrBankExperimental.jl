```
nsoli(F!, x0, FS, FPS, Jvec=dirder; rtol=1.e-6, atol=1.e-12,
           maxit=20, lmaxit=-1, lsolver="gmres", eta=.1,
           fixedeta=true, Pvec=nothing, pside="right",
           armmax=10, dx = 1.e-7, armfix=false, pdata = nothing,
           printerr = true, keepsolhist = false, 
           Krylov_Data = nothing, stagnationok=false)
```

)

C. T. Kelley, 2022

私のSIAMの本からの非線形ソルバーのJuliaバージョン。ここに：nsoli

関数とKrylov基底のストレージを事前に割り当てる必要があります –> 呼び出しプログラム内 <– つまり、FSとFPS内で

入力：

  * F!: 関数評価、!はF!がFSを上書きすることを示し、これは関数のための事前に割り当てられたストレージです。

    したがって、FS=F!(FS,x)またはFS=F!(FS,x,pdata)はFS=F(x)を返します。

    あなたの関数は必ず –> FSを返す <– 必要があります。ドキュメントの例を参照してください。
  * x0: 初期反復
  * FS: 関数のための事前に割り当てられたストレージ。サイズNのベクトルです。

    (N)として保存し、F!をサイズ(N)のベクトルを使用するように設計する必要があります。(N,1)を一貫して使用した場合、ソルバーは動作するかもしれませんが、保証はしません。
  * FPS: Krylov基底のための事前に割り当てられたストレージ。これはN x mの行列で、再起動前に最大m-1のGMRES反復を行う予定です。
  * Jvec: ヤコビアンベクトル積。これを省略すると、デフォルトは有限差分方向微分です。

    したがって、FP=Jvec(v,FS,x)またはFP=Jvec(v,FS,x,pdata)はFP=F'(x) vを返します。

    (v, FS, x)または(v, FS, x, pdata)が引数リストでなければなりません。たとえFPがFSを必要としなくても。これには、有限差分微分が必要であり、それがソルバーのデフォルトであるという理由があります。
  * 精度：精度についてお話ししましょう。このコードは、あなたが望む任意の精度で完全な精度の関数と線形代数のために設計しました。FPSをFloat64またはFloat32として宣言すると、nsoliは正しいことを行います。Float16のサポートはありますが、うまく機能していません。

    ヤコビアンが適切に条件付けされている場合、直交化とストレージ（GMRES用）のコストを半分に削減できますが、損失はありません。線形ソルバーがGMRESでない場合や、Krylovベクトルの直交化とストレージが計算コストの小さな部分である場合、利点はありません。したがって、前処理器が良好で、いくつかのKrylovs/Newtonが必要な場合、精度を下げてもあまり役に立ちません。

    BiCGSTABは、精度を下げても利益を得ません。

---

キーワード引数（kwargs）：

rtolおよびatol：相対および絶対誤差許容値

maxit：非線形反復の制限

lmaxit：線形反復の制限。lmaxit > m-1の場合、FPSにm列があり、m-1以上の線形反復が必要な場合、GMRESは再起動します。

デフォルトはGMRESのために-1です。これは、サイズ(V) = (n,m)のm-1反復を行い、再起動なしで行うことを意味します。BiCGSTABのデフォルトは10です。

lsolver：線形ソルバー、デフォルト = "gmres"

あなたの選択肢は「gmres」または「bicgstab」です。ただし、現時点ではgmresが唯一のオプションです。

etaおよびfixed eta：eta > 0またはエラーがあります。

線形ソルバーは、||F'(x)s + F(x) || <= etag || F(x) ||のときに終了します。

ここで

etag = eta（fixedeta=trueの場合）

etag = Eisenstat-Walker（fixedeta=falseの場合）として本に実装されています。

デフォルトは、変更される可能性がありますが、eta=.1、fixedeta=trueです。

Pvec：前処理器-ベクトル積。ルールはJvecに似ています。したがって、Pv=Pvec(v,x)またはPv=Pvec(v,x,pdata)はP(x) vを返します。P(x)は前処理器です。前処理器がxに依存しない場合でも、xを入力として使用する必要があります。

pside：psideで前処理器を適用、デフォルト = "right"。私は「left」を推奨しません。この件については第3章を参照してください。

armmax：ラインサーチにおけるステップサイズの減少の上限

dx：デフォルト = 1.e-7

有限差分微分における差分増分h=dx*norm(x,Inf)+1.e-8

armfix：デフォルト = false

デフォルトは放物線ラインサーチ（つまりfalse）です。trueに設定すると、ステップサイズは0.5に固定されます。これは、研究のための実験を行っている場合を除いて、行わないでください。

pdata：

関数、ヤコビアン-ベクトル、および前処理器-ベクトル積のための事前計算データ。関数/ヤコビアン内のグローバル変数にデータを隠すのではなく、これを使用すると、物事がうまくいきます。

F!、Jvec、またはPvecのいずれかでpdataを使用する場合は、すべてで使用する必要があります。

printerr：デフォルト = true

ソルバーが失敗したときに役立つメッセージを印刷します。そのメッセージを抑制するには、printerrをfalseに設定します。

keepsolhist：デフォルト = false

これをtrueに設定すると、出力タプルに反復の履歴が得られます。これはスカラー方程式のデフォルトでオンであり、システムではオフです。データが本当に大きくなる可能性があるため、データを使用する必要がある場合にのみオンにしてください。

Krylov_Data：デフォルト = nothing

これは、ソルバーの内部ストレージを格納する構造体です。nkl_init関数で自分で事前に割り当てることができますが、そうすべきではないかもしれません。

Krylov_Data 

= nkl_init(n,lsolver)

これは扱うのが危険なものであり、nsoliの割り当てが継続またはIVP統合の問題になる場合にのみ推奨します。Krylov_Dataは、反復の最後に解を格納する場所であり、解を他の場所にコピーせずに再利用すると、失われ、新しい解で上書きされます。継続ケーススタディはこれを使用しており、私が何をしたかを見るためにそれを確認する必要があります。

stagnationok：デフォルト = false

ラインサーチを無効にし、発散または停滞を観察したい場合は、これをtrueに設定します。これは、研究や本を書くためにのみ役立ちます。

出力：

  * 名前付きタプル (solution, functionval, history, stats, idid,              errcode, solhist)

ここで

– solution = 収束した結果

– functionval = F(solution)

– history = 反復の残差ノルムのベクトル (||F(x)||)

– stats = (ifun, ijac, iarm, ikfail)の履歴の名前付きタプル、各反復での関数/ヤコビアン-ベクトル積/ステップ長の減少/線形ソルバーの失敗の数。線形ソルバーの失敗は、非線形ソルバーが失敗することを意味しません。たとえば、ラインサーチが失敗した場合は、この統計を確認する必要があります。FPSと/またはlmaxitのサイズを増やすことで問題が解決するかもしれません。

有限差分微分の関数値は、ヤコビアン-ベクトル積にカウントされないため、カウントしません。

– idid=trueは反復が成功した場合、falseはそうでない場合。

– errcode = 0は反復が成功した場合

```
    = -1は初期反復が終了基準を満たす場合

    = 10はmaxit反復後に収束しない場合

    = 1はラインサーチが失敗した場合
```

– solhist：

```
  これは、keepsolhist=trueに設定した場合の反復の全履歴です。
```

solhistはN x Kの配列で、Nはxの長さ、Kは反復の数+1です。したがって、スカラー方程式の場合、それは行ベクトルです。

---

### nsoliの例

#### 簡単な2D問題。

nsol.jlと同じ結果が得られるはずです。なぜなら、GMRESは正確に2回の反復で方程式を解くからです。有限差分ヤコビアンと解析ヤコビアン-ベクトル積は、完全な精度と有限差分ヤコビアン-ベクトル積は単精度です。

BiCGSTABは5回の反復で収束し、各非線形反復は2つのヤコビアン-ベクトル積を必要とします。GMRESのKrylov空間のストレージ（jvs）は、BiCGSTABが線形ソルバーである場合、単一のベクトル（fpv）に置き換えられます。

```jldoctest
julia> function f!(fv,x)
       fv[1]=x[1] + sin(x[2])
       fv[2]=cos(x[1]+x[2])
       return fv
       end
f! (generic function with 1 method)

julia> function JVec(v, fv, x)
       jvec=zeros(2);
       p=-sin(x[1]+x[2])
       jvec[1]=v[1]+cos(x[2])*v[2]
       jvec[2]=p*(v[1]+v[2])
       return jvec
       end
JVec (generic function with 1 method)

julia> x0=ones(2); fv=zeros(2); jv=zeros(2,2); 

julia> jv32=zeros(Float32,2,2);

julia> jvs=zeros(2,3); jvs32=zeros(Float32,2,3);

julia> nout=nsol(f!,x0,fv,jv; sham=1);

julia> kout=nsoli(f!,x0,fv,jvs,JVec; 
                  fixedeta=true, eta=.1, lmaxit=2);

julia> kout32=nsoli(f!,x0,fv,jvs32; 
                    fixedeta=true, eta=.1, lmaxit=2);

julia> [nout.history kout.history kout32.history]
5×3 Array{Float64,2}:
 1.88791e+00  1.88791e+00  1.88791e+00
 2.43119e-01  2.43120e-01  2.43119e-01
 1.19231e-02  1.19231e-02  1.19230e-02
 1.03266e-05  1.03261e-05  1.03264e-05
 1.46388e-11  1.40862e-11  1.39825e-11

julia> fpv=zeros(2);

julia> koutb=nsoli(f!,x0,fv,fpv,JVec; 
            fixedeta=true, eta=.1, lmaxit=2, lsolver="bicgstab");

julia> koutb.history
6-element Vector{Float64}:
 1.88791e+00
 2.43120e-01
 1.19231e-02
 4.87500e-04
 7.54236e-06
 3.84646e-07
```
