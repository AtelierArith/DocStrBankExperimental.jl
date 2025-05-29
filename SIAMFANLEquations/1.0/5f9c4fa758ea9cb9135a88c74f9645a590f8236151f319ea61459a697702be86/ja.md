nsolsc(f,x0, fp=difffp; rtol=1.e-6, atol=1.e-12, maxit=10,         solver="newton", sham=1, armmax=10, resdec=.1, dx=1.e-7,         armfix=false, pdata=nothing,         printerr=true, keepsolhist=true, stagnationok=false)

C. T. Kelley, 2022

スカラー方程式のためのニュートン法。方程式系のコードに必要なほとんどの機能を備えています。これは、システムの実際のコードであるnsol.jlへの呼び出しのラッパーです。

入力:

f: 関数

x0: 初期反復値

fp: 導関数。導関数がfpである場合、その名前を教えてください。たとえば、fp=foobarは、foobarがあなたの導関数の関数であることを示します。デフォルトは、私が提供する前方差分ヤコビアンです。

キーワード引数 (kwargs):

rtol, atol: 実数および絶対誤差許容値

maxit: 非線形反復の最大数の上限

solver:

選択肢は「newton」（デフォルト）または「chord」です。ただし、shamはnewtonを選択した場合にのみ利用可能です。「chord」は、反復が収束するまで初期導関数を使用し続け、反復予算を使用するか、線形探索が失敗するまで使用します。これは、sham=Infとは異なり、よりスマートです。

セカント法を使用し、初期反復値が不適切な場合は、間違いを犯しています。有限差分導関数で線形探索を駆動することでお手伝いします。

sham:

これはシャマンスキー法です。sham=1の場合、ニュートン法を使用します。反復は、sham回数ごとに導関数を更新します。収束率は、導関数を更新する反復のみをカウントした場合、局所的なq次数sham+1を持ちます。このオプションを使用するには、自分の導関数を提供する必要はありません。sham=Infは、chordがうまく収束している場合のみchordです。

armmax: 線形探索におけるステップサイズの減少の上限

resdec: 残差減少の目標値。

デフォルト値は.1です。古いMATLABコードでは.5でした。残差が急速に減少している場合、少なくともresdecの因子で、線形探索が静止している場合にのみ、シャマンスキーをオンにします。このメソッドからresdecを排除したい場合（したくないですが）、resdec = 1.0に設定すると、二度と聞くことはありません。

dx:

これは前方差分の増分で、デフォルトは1.e-7です。dxは関数のノイズの平方根に近い必要があります。

armfix:

デフォルトは放物線線形探索（つまりfalse）です。trueに設定すると、ステップサイズは.5に固定されます。研究のための実験を行っている場合を除いて、これを行わないでください。

pdata:

関数/導関数のための事前計算データ。このオプションを使用すると、関数/導関数内のグローバル変数にデータを隠すよりも、うまくいきます。このオプションを使用する場合、関数と導関数はpdataを第二引数として受け取る必要があります。例: f(x,pdata) および fp(x,pdata)

printerr:

ソルバーが失敗したときに役立つメッセージを印刷します。そのメッセージを抑制するには、printerrをfalseに設定します。

keepsolhist:

出力タプルに反復の履歴を取得するには、これをtrueに設定します。これはスカラー方程式の場合はデフォルトでオンで、システムの場合はオフです。データが本当に大きくなる可能性があるため、データを使用する場合にのみオンにしてください。

stagnationok:

線形探索を無効にし、発散または停滞を観察したい場合は、これをtrueに設定します。これは研究や書籍執筆にのみ役立ちます。

出力:

名前付きタプル (solution, functionval, history, stats, idid,                errcode, solhist) で、ここで

solution = 収束した結果 functionval = F(solution) history = 反復の残差ノルムのベクトル (||F(x)||) stats = 各反復での関数/導関数/ステップ長の減少の数を示す履歴の名前付きタプル (ifun, ijac, iarm)。

有限差分導関数のための関数値は、ヤコビアン評価にカウントされるため、カウントしません。セカント法モデルのためにはカウントします。

idid=true は反復が成功した場合、false はそうでない場合。

errcode = 0 反復が成功した場合         = -1 初期反復値が終了基準を満たす場合         = 10 maxit反復後に収束しない場合         = 1  線形探索が失敗した場合

solhist:

これが、keepsolhist=trueに設定した場合の反復の全履歴です。

nsolscは、Toolsディレクトリの関数を使用してsolhistを構築します。システムの場合、solhistはN x Kの配列で、Nはxの長さ、Kは反復数+1です。したがって、スカラー方程式の場合 (N=1)、solhistは行ベクトルです。したがって、以下の例でのsolhist'の使用です。

### nsolsc.jlの例

```jldoctest
julia> nsolout=nsolsc(atan,1.0;maxit=5,atol=1.e-12,rtol=1.e-12);

julia> nsolout.history
6-element Array{Float64,1}:
 7.85398e-01
 5.18669e-01
 1.16332e-01
 1.06102e-03
 7.96200e-10
 2.79173e-24
```

# 解析的導関数がある場合、私はそれを使用します。

```jldoctest
julia> fs(x)=x^2-4.0; fsp(x)=2x;

julia> nsolout=nsolsc(fs,1.0,fsp; maxit=5,atol=1.e-9,rtol=1.e-9);

julia> [nsolout.solhist'.-2 nsolout.history]
6×2 Array{Float64,2}:
 -1.00000e+00  3.00000e+00
  5.00000e-01  2.25000e+00
  5.00000e-02  2.02500e-01
  6.09756e-04  2.43940e-03
  9.29223e-08  3.71689e-07
  2.22045e-15  8.88178e-15

```

# 無名関数も使用できます

```jldoctest
julia> nsolout=nsolsc(atan,10.0,x -> 1.0/(1.0+x^2); 
atol=1.e-9,rtol=1.e-9);

julia> nsolout.history
8-element Vector{Float64}:
 1.47113e+00
 1.19982e+00
 1.10593e+00
 6.48297e-01
 2.56983e-01
 1.19361e-02
 1.13383e-06
 9.71970e-19
```
