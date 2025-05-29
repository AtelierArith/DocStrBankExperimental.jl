bioclimAE(bc::Worldclim_bioclim, maxbud::Unitful.Quantity{Float64}, area::Unitful.Area{Float64})

`ContinuousHab`、`SimpleBudget`型の非生物環境をWordclim型気候から作成するための関数です。これは、最大予算値`maxbud`で満たされた`SimpleBudget`型を作成するか、提供された`SolarBudget`型の予算を使用します。アクティブなグリッドセルのBool行列`active`が含まれている場合はこれを使用し、そうでない場合はすべてのグリッドセルがアクティブなものが作成されます。
