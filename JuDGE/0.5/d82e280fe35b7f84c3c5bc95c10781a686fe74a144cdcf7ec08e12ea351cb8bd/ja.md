Termination(;abstol::Real=10^-9,             reltol::Real=10^-9,             rlx*abstol::Real=10^-9,             rlx*reltol::Real=10^-9,             time*limit::Real=Inf,             max*iter::Int=typemax(Int),             inttol::Real=10^-8,             allow*frac::Symbol=:binary*solve)

`JuDGE.solve()` / `JuDGE.branch_and_price()`の停止条件を定義します。

### オプション引数

`abstol`は、最良の整数実現可能な目的値と下限に対する絶対許容誤差です。

`reltol`は、最良の整数実現可能な目的値と下限に対する相対許容誤差です。

`rlx_abstol`は、緩和されたマスター目的値と下限に対する絶対許容誤差です。

`rlx_reltol`は、緩和されたマスター目的値と下限に対する相対許容誤差です。

`time_limit`は、最大の持続時間（秒）です。

`max_iter`は、最大の反復回数です。

`inttol`は、整数実現可能な解に対する任意のバイナリ/整数変数の0または1からの最大偏差です。

`allow_frac`は、分数解が返されるかどうかを示します。可能な値は次のとおりです：     `:binary_solve`は、解が返される前にマスターのバイナリ解が実行されます（必要に応じて）；     `:binary_solve_return_relaxation`は、マスターのバイナリ解が実行され（必要に応じて）、上限が更新されますが、マスター問題の関係が返されます；     `:first_fractional`は、見つかった最初の分数マスター解を返します；     `:no_binary_solve`は、終了時に緩和されたマスター問題の解を単に返します。

### 例

Termination(rlx_abstol=10^-6)    Termination(abstol=10^-3,inttol=10^-6)
