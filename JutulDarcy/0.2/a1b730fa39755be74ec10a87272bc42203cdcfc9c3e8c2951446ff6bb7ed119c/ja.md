```
ws, states = simulate_mrst_case(file_name)
simulate_mrst_case(file_name; <keyword arguments>)
```

`writeJutulInput`によってMRSTからエクスポートされた`file_name`からMRSTケースをシミュレートします。

# 引数

  * `file_name::String`: シミュレーション対象の`.mat`または`.data`ファイルへのパス。

# キーワード引数

  * `extra_outputs::Vector{Symbol} = [:Saturations]`: シミュレーションから出力する追加の変数。
  * `write_output::Bool = true`: 出力を記録する（デフォルトのJLD2形式で）
  * `output_path = nothing`: 出力ファイルのディレクトリ。このディレクトリの下にファイルが書き込まれます。デフォルトは`file_name`のフォルダです。
  * `write_mrst = true`: 完了したシミュレーションの後にMRST互換の出力を書き込む。これはMRSTの`readJutulOutput`で読み取ることができます。
  * `backend=:csc`: 線形システムのバックエンドの選択。デフォルトのJuliaスパース用の`:csc`、実験的な並列CSR用の`:csr`。
  * `verbose=true`: 呼び出し時にこのルーチンに特有の追加情報を印刷する
  * `nthreads=Threads.nthreads()`: 使用するスレッドの数
  * `linear_solver=:bicgstab`: 使用するKrylov.jlソルバーの名前、または小さなケースのみのための:direct
  * `info_level=0`: 標準のJutul info_level。最小限の印刷のための0、印刷しないための-1、さまざまな冗長性レベルのための1-5

追加の入力引数は、[`setup_case_from_mrst`](@ref)、[`setup_reservoir_simulator`](@ref)、および[`simulator_config`](@ref)に渡されます（該当する場合）。
