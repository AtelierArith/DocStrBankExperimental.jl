```
PDMPProblem(F, R, Delta, nu, xc0, xd0, p, tspan)
```

PDMP問題をシミュレーションするために作成します。PDMP問題を定義するには、まずODEを定義する関数`F`と初期条件`xc0`を指定する必要があります：dxc/dt = F(xc(t),xd(t),p,t)。ジャンプは、あるレート`R`で状態を変化させるジャンプロセスとして定義されます。ジャンプの間、`xd`は一定ですが、`xc`は進化することが許可されています。

## 引数

  * `F`: ベクトル場を表すインプレース関数`F(du, u, p, t)`
  * `R`: 遷移レートを計算する関数。インプレースとして`R(rate::AbstractVector, xc, xd, p, t, issum::Bool)`で指定する必要があり、`rate`を変更します。ブール値`issum`が提供され、`R`の動作は次のようになります。

    1. `issum == true`の場合、`R`は合計レートのみを返す必要があります。*例*：`sum(rate)`。これは、時には`rate`を変更せずに`sum`を計算できるため、この形式を使用します。
    2. `issum == false`の場合、`R`は更新されたレートで`rate`を埋める必要があります。

次に、ジャンプが状態変数にどのように影響するかを提供する必要があります。ここには2つの可能な方法があります：     1. 遷移行列`nu`を与える：これは離散成分`xd`にのみ影響し、`xc`には影響を与えません。     2. ジャンプを実装する関数`Delta(xc, xd, parms, t, ind_reaction::Int64)`を与える。ここで`xc,xd`または`parms`を変更できます。引数`ind_reaction`は、ジャンプが発生する反応のインデックスです。例については`examples/pdmp_example_eva.jl`を参照してください。

  * `Delta` [オプション]: ジャンプを実行する関数
  * `nu` [オプション]: 遷移行列
  * `xc0`: 連続部分の初期条件
  * `xd0`: 離散部分の初期条件
  * `p`: 関数`F, R, Delta`に提供されるパラメータ
  * `tspan`: 問題の時間範囲。

## コンストラクタ

  * `PDMPProblem(F,R,Delta,nu,xc0,xd0,p,tspan)`
  * `PDMPProblem(F,R,nu,xc0,xd0,p,tspan)` は、関数`Delta`を提供したくない場合
  * `PDMPProblem(F,R,Delta,reaction_number::Int64,xc0,xd0,p,tspan)` は、遷移行列`nu`を提供したくない場合。レートベクトルの長さ`reaction_number`を提供する必要があります。

また、[JumpProcesses.jl](https://github.com/SciML/JumpProcesses.jl)へのラッパーも提供しています。これは、`JumpProblem`が作成される方法に非常に似ています。

  * `PDMPProblem(prob, jumps...)` ここで`prob`は`ODEProblem`である可能性があります。例については、`example/examplediffeqjumpwrapper.jl`を考慮してください。

```
