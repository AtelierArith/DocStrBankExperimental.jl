secant(f,x0; rtol=1.e-6, atol=1.e-12, maxit=10,         armmax=10, armfix=false, pdata=nothing,         printerr=true, keepsolhist=true, stagnationok=false)

C. T. Kelley, 2022

スカラ方程式のためのセカント法。

入力:

f: 関数

x0: 初期反復値

キーワード引数 (kwargs):

rtol, atol: 実数および絶対誤差許容値

maxit: 非線形反復の最大数の上限

セカント法を使用し、初期反復値が不適切な場合は、間違いを犯しています。エラーメッセージが表示されます。

armmax: ラインサーチにおけるステップサイズの減少の上限

armfix:

デフォルトは放物線ラインサーチです（すなわち、false）。trueに設定すると、ステップサイズは0.5に固定されます。研究のための実験を行っている場合を除き、これを行わないでください。

printerr:

ソルバーが失敗したときに役立つメッセージを印刷します。そのメッセージを抑制するには、printerrをfalseに設定します。

keepsolhist:

出力タプルに反復の履歴を取得するには、これをtrueに設定します。これはスカラ方程式の場合はデフォルトでオンで、システムの場合はオフです。データが本当に大きくなる可能性があるため、必要な場合のみオンにしてください。

stagnationok:

ラインサーチを無効にし、発散または停滞を観察したい場合は、これをtrueに設定します。これは研究や書籍執筆のためにのみ有用です。

出力:

名前付きタプル (solution, functionval, history, stats, idid,                errcode, solhist) であり、

solution = 収束した結果 functionval = F(solution) history = 反復の残差ノルムのベクトル (||F(x)||) stats = 各反復における関数/導関数/ステップ長の減少の数の履歴の名前付きタプル (ifun, ijac, iarm)。セカント法の場合、ijac = 0。

idid=true は反復が成功した場合、false はそうでない場合。

errcode = 反復が成功した場合は0         = 初期反復値が終了基準を満たす場合は-1         = maxit反復後に収束しなかった場合は10         = ラインサーチが失敗した場合は1

solhist:

keepsolhist=true に設定した場合の反復の全履歴です。

secantは、Toolsディレクトリの関数を使用してsolhistを構築します。システムの場合、solhistはN x Kの配列で、Nはxの長さ、Kは反復数+1です。したがって、スカラ方程式の場合 (N=1)、solhistは行ベクトルです。したがって、以下の例でのsolhist'の使用。

### secant.jlの例

```jldoctest

julia> secout=secant(atan,1.0;maxit=6,atol=1.e-12,rtol=1.e-12);


julia> secout.history
7-element Array{Float64,1}:
 7.85398e-01
 5.18729e-01
 5.39030e-02
 4.86125e-03
 4.28860e-06
 3.37529e-11
 2.06924e-22
```
