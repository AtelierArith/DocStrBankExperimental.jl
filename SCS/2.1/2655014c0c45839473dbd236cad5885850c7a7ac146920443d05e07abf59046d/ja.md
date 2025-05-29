```
scs_solve(linear_solver, args...)
```

SCSソルバーへの低レベルインターフェースです。

!!! warning
    この関数は、誤った使用のリスクを伴う高度な機能です。新しいユーザーの場合は、代わりにJuMPまたはConvexインターフェースを使用することをお勧めします。


## 問題定義

SCSは次の形式の問題を解決します。

```
minimize        1/2 * x' * P * x + c' * x
subject to      A * x + s = b
                s in K
```

ここで、Kは次のような積円錐です。

  * ゼロ円錐
  * 正の直交体 `{ x | x ≥ 0 }`
  * ボックス円錐 `{ (t,x) | t*l ≤ x ≤ t*u }`
  * 二次円錐 (SOC) `{ (t,x) | ||x||_2 ≤ t }`
  * 半正定値円錐 (SDC) `{ X | X is psd }`
  * 指数円錐 `{ (x,y,z) | y e^(x/y) ≤ z, y > 0 }`
  * 幂円錐 `{ (x,y,z) | x^a * y^(1-a) ≥ |z|, x ≥ 0, y ≥ 0 }`
  * 双対幂円錐 `{ (u,v,w) | (u/a)^a * (v/(1-a))^(1-a) ≥ |w|, u ≥ 0, v ≥ 0 }`

## 入力引数

問題データは次のとおりです。

  * `linear_solver`: 使用する `LinearSolver`
  * `m`: アフィン制約の数
  * `n`: 変数の数
  * `A`: `m` 行 `n` 列の `AbstractMatrix`
  * `P`: サイズ `(n, n)` の正定値対称行列の上三角成分
  * `b`: 長さ `m` の `Vector`
  * `c`: 長さ `n` の `Vector`

`A` の行は `K` の円錐に対応し、次の引数で上記の順序で指定する必要があります。

  * `z`: プライマルゼロ / 双対自由円錐の数、すなわちプライマル等式制約
  * `l`: 線形円錐の数
  * `bu`: ボックス円錐の上限の `Vector`
  * `bl`: ボックス円錐の下限の `Vector`
  * `q`: SOCのサイズの `Vector`
  * `s`: SDCのサイズの `Vector`
  * `ep`: プライマル指数円錐の数
  * `ed`: 双対指数円錐の数
  * `p`: 幂円錐パラメータの `Vector` (±1、双対円錐には負の値)

次のようにしてSCSにウォームスタートを提供します。

  * `primal_sol = zeros(n)`: プライマル変数をウォームスタートするための `Vector`、
  * `dual_sol = zeros(m)`: 双対変数をウォームスタートするための `Vector`、
  * `slack = zeros(m)`: スラック変数をウォームスタートするための `Vector`。

!!! note
    ソルバーを正常にウォームスタートするには、`primal_sol`、`dual_sol`、および `slack` をすべて提供する必要があり、`warm_start` オプションを `true` に設定する必要があります。


最後に、いくつかのキーワード引数をソルバーへのオプションとして渡すことができます。有効なキーワードは `fieldnames(ScsSettings)` です。各キーワードに関する情報は公式のSCSドキュメントを参照してください。

## 出力

この関数は、次のフィールドを含む `Solution` オブジェクトを返します。

```julia
mutable struct Solution{T}
    x::Vector{Float64}
    y::Vector{Float64}
    s::Vector{Float64}
    info::ScsInfo{T}
    ret_val::T
end
```

ここで、`x` はプライマル変数の最適値を格納し、`y` は双対変数の最適値を格納し、`s` はスラック変数であり、`info` は解決ステップに関するさまざまな情報を含みます。

!!! warning
    SCSは半正定値円錐が√2の因子でスケーリングされることを期待しています。つまり、A行列のオフダイアゴナル要素とbベクトルは√2で乗算され、その後、双対およびスラックソリューションベクトルの対応する行は1/√2で乗算されるべきです。


`SCS.raw_status(::ScsInfo)::String` は状態を説明します。例: `"solved"`、`"infeasible"`、`"unbounded"` など。正確な戻りステータスについては、`ret_val` フィールドの値を https://github.com/cvxgrp/scs/blob/3aaa93c7aa04c7001df5e51b81f21b126dfa99b3/include/glbopts.h#L18 と比較する必要があります。
