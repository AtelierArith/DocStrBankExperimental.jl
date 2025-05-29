```
linsystems, ssys = trajectory_ss(sys, inputs, outputs, sol; t = _max_100(sol.t), fuzzer=nothing, verbose = true, kwargs...)
```

`sys`を軌道`sol`の周りで時刻`t`に線形化します。`StateSpace`オブジェクトのベクトルと簡略化されたシステムを返します。

# 引数:

  * `inputs`: 変数または分析ポイントのベクトル。
  * `outputs`: 変数または分析ポイントのベクトル。
  * `sol`: ODE解オブジェクト。この解は簡略化されたシステムの状態を含む必要があり、`sol(t, idxs=x)`のように`idxs`引数を通じてアクセスできます。
  * `t`: 線形化する解の軌道に沿った時点。返される`StateSpace`オブジェクトの配列は`t`と同じ長さになります。
  * `fuzzer`: 操作点辞書を受け取り、「ファズ」された操作点の配列を返す関数。これは、軌道に沿った操作点にノイズ/不確実性を追加するのに役立ちます。こうした関数については[`ControlSystemsMTK.fuzz`](@ref)を参照してください。
  * `verbose`: `true`の場合、`sol`に見つからない変数の警告を表示します。
  * `kwargs`: 線形化関数に送信されます。
