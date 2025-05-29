eraAE(era::ERA, maxbud::Unitful.Quantity{Float64})

ERA型気候から`ContinuousHab`、`SimpleBudget`型の非生物環境を作成する関数です。これは、最大予算値`maxbud`で満たされた`SimpleBudget`型を作成するか、提供された`SolarTimeBudget`型の予算を使用します。アクティブなグリッドセルのBool行列`active`が含まれている場合、これが使用されます。そうでない場合は、すべてのグリッドセルがアクティブなものが作成されます。
