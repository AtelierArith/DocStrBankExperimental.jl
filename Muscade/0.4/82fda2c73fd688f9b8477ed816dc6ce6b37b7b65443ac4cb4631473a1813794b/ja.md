```
solve(Solver;dbg=(;),verbose=true,silenterror=false,kwargs...)
```

`Solver`を使用して分析を実行し、エラーが発生した場合に部分的な結果を保護します。

# 名前付き引数

  * `dbg=(;)`           コールツリーをトレースするための名前付きタプル（デバッグ用）
  * `verbose=true`      出力を抑制するにはfalseに設定（テスト用）
  * `silenterror=false` エラーの出力を抑制するにはtrueに設定（テスト用）
  * `kwargs...`         ソルバーによって提供されるメソッド`solve`に渡されるさらなる引数

これは、ソルバーによって提供されるメソッド`solve`を`solve(Solver,pstate,verbose,(dbg...,solver=Symbol(Solver));kwargs...)`で呼び出します。

関連情報: [`SweepX`](@ref), [`DirectXUA`](@ref), [`initialize!`](@ref) 
