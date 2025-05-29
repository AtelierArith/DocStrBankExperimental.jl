```
NLLSsolver.optimize!(problem::NLLSProblem, options=NLLSOptions(), 
                     unfixed=nothing, callback=nullcallback)
```

`problem`で定義されたコストを最適化し、変数をインプレースで更新し、`result::NLLSResult`を返します。

どの最適化手法を使用するかや終了基準などのオプションは、`options::[`NLLSOptions`](@ref)`で定義できます。デフォルトのオプションは、Levenberg-Marquardt最適化を指定します。

すべての変数を最適化する必要がない場合は、`unfixed`を使用して、最適化すべき固定されていない変数を定義できます。これは、単一の変数の整数インデックス、変数の型、またはブールベクトルである可能性があります。デフォルト（`nothing`）は、すべての変数を最適化する必要があることを示します。

コールバック関数は、`callback`引数を介して提供できます。この関数は、最適化の各イテレーションの後に呼び出され、次の形式を取る必要があります：`julia     cost, terminate = callback(cost, problem, data::NLLSInternal, iteratedata)``ここで`cost`は（コールバックが問題を更新した場合）潜在的に更新された問題コストであり、`terminate`は整数で、非ゼロの値は最適化手法が終了すべきことを示します。`terminate`の値は、`optimizer!`の結果に報告されます。デフォルトの[`nullcallback`](@ref)は何もしません。既存のコールバック[`printoutcallback`](@ref)と[`storecostscallback`](@ref)は、それぞれイテレーションごとの情報を出力および保存します。コールバックはユーザー定義も可能です。

変数はインプレースで最適化され、`problem::`[`NLLSProblem`](@ref)の`variables`要素は見つかった最適値に設定されます。開始および終了コスト、イテレーション数、高レベルのタイミング、終了理由などの他の関連情報は、[`NLLSResult`](@ref)オブジェクトに返されます。
