```
define_problem(; linear =["prices"], nonlinear = [""],
    cov = "all" or Vector{Tuple{String,String}},  # "all"を受け入れて非線形を自動ペアリング
    data, fixed_effects = [""],
    se_type = "bootstrap",
    cluster_var = "", constrained::Bool = false,
    drop_singletons = true, gmm_steps = 2, method = :cpu)
```

この関数はFRAC問題オブジェクトを構築するために使用されます。主な入力はデータ、線形および非線形の共変量、固定効果であり、すべて文字列のベクトルとして指定されます。ユーザーは使用する標準誤差のタイプ、クラスタ変数、モデルが制約されているかどうか、および使用するGMMステップの数を指定することもできます。現在、`method`は使用されていません。
