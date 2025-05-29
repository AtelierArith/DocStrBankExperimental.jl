worldclimAE(wc::Worldclim_monthly, maxbud::Unitful.Quantity{Float64})

`ContinuousTimeHab`、`SimpleBudget`型の非生物環境をWordclim型気候から作成する関数です。これは、最大予算値`maxbud`で満たされた`SimpleBudget`型を作成するか、提供された`SolarTimeBudget`型の予算を使用します。アクティブなグリッドセルのBool行列`active`が含まれている場合、これが使用されます。そうでない場合は、すべてのグリッドセルがアクティブと見なされます。
