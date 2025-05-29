```
run_dice(pars;optimizer,bounds)
run_dice(;optimizer,bounds,kwargs...)
```

D(R)ICEモデルを実行します（現在の構造とデフォルトでDICE2023のデータを使用）、カスタムオプティマイザ、境界、またはパラメータを使用することも可能です。

この関数はDICEモデルを実行し、結果を名前付きタプルとして返します。DICEModel v0.2以降、地域次元は常に存在し、DICEは単一地域のRICEとして単純に扱われます。

# 関数引数

## 位置引数:

  * `pars`: 必要なパラメータを含む[`DICEParameters`](@ref)構造体のインスタンス

## キーワード引数:

  * `optimizer`: 使用するオプティマイザとそのオプション。デフォルトは次の通りです: [`optimizer = optimizer_with_attributes(Ipopt.Optimizer,"print_level" => 0, "max_wall_time"=>10.0^20, "max_cpu_time" => 10.0^20, "max_iter" => 3000, "acceptable_tol" =>10^-6, "acceptable_iter" => 15, "acceptable_dual_inf_tol" =>10.0^10, "acceptable_constr_viol_tol" => 0.01, "acceptable_compl_inf_tol" =>0.01, "acceptable_obj_change_tol" =>10.0^20)`]。印刷レベルを除いて、すべてはIpoptのデフォルトです。
  * `bounds`: 等式または不等式制約の辞書。各制約は、変数名をキー、2要素のタプルを値として指定する必要があります。最初の要素は"<="、">="、または"=="のいずれかであり、2番目の要素は制約の右辺（単一の値、ntimesteps長のベクトル、またはntimesteps x nregionsの行列）です。デフォルト: （空の辞書）。モデル変数の名前については[ソースコード](https://github.com/sylvaticus/DICEModel.jl/blob/main/src/DICEModel.jl)を参照してください。
  * `kwargs`: DICE2023のデフォルトパラメータ値を上書きするためのキーワード引数。利用可能なモデルパラメータについては[`DICEParameters`](@ref)構造体のドキュメントを参照してください。

**警告**: 時々、パラメータを変更しても期待される動作にはならないことがあります。これは、モデル（このパッケージで再実装された元のGAMS形式）がパラメータでいくつかのキャリブレーションを行うため、いくつかのパラメータを一緒に変更する必要があるからです。たとえば、異なる割引率をテストするすべてのシナリオは、`prstp`パラメータだけを変更するのではなく、他のいくつかのパラメータを計算し、時にはデフォルトモデルとは異なる方法で、初期条件の異なるキャリブレーションを持ちます。変更したいパラメータがモデルに他の副作用を持たないことを確認するために、常に[ソースコード](https://github.com/sylvaticus/DICEModel.jl/blob/main/src/CoreModel.jl)を確認してください。

# 出力

  * `solved`、`status`、`times`、`tidx`、ポストプロセスで計算された値、最適化変数、パラメータ構造（`pars`）を含む名前付きタプル。

# 例:

```Julia
res = run_dice()
ECO2_opt = res.ECO2
plot(res.times[1:11] .+ 2020,ECO2_opt[1:11],ylim=(0,80), title="CO₂ emissions",ylabel="GtCO₂/yr",label="C/B optimal", markershape=:circle, markercolor=:white)
```

```Julia
res_crazy = run_dice(optimizer=optimizer_with_attributes(Ipopt.Optimizer,"print_level" => 0), bounds = Dict("MIU"=>("==",1.0), "TATM"=>("<=",15), "Y" =>(">=",[fill(floatmin(Float64),10);fill(0.1,71)]), "ECO2" =>("<=",10000)), a2base = 0.01)
```

```julia
w_dev_country_priority = [1,1,1,1.5,2,2,3,3,2,5,5,5] # 地域ごとの効用重み
res_12regions_devprior = run_dice(RICE2023(;weights=w_dev_country_priority))
```

# 注意事項

  * `bounds`は問題に制約を追加しますが、モデル内のハードコーディングされた境界を置き換えるものではありません。特に、排出制御の上限には`miuup`パラメータを使用する必要があります。
  * 境界は常に全時間ステップを対象としています。時間ステップのサブセット（例：最初の時間ステップ）のための境界が必要な場合は、適切に`floatmin(Float64)`または`floatmax(Float64)`を使用して、境界の完全な時間配列を組み立てる必要があります。
  * キーワード引数を持つバージョンは、パラメータ構造を持つバージョンを呼び出す小さなラッパーです。これは、提供されたキーワード引数を使用して`DICE2023`関数で構築されます。
  * [`DICEParameters`](@ref)構造体で使用される重みは外生的であり、ネギシ重みではありません。`run_dice`関数は、これらの重みを探すためにインタラクティブに使用されることがあります。
