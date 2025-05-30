```
ODEIntegrator
```

基本的な `struct` で、微分方程式の数値解法をインタラクティブにステップ実行することを可能にします。完全なドキュメントはここにホストされています: [https://diffeq.sciml.ai/latest/basics/integrator/](https://diffeq.sciml.ai/latest/basics/integrator/)。このドキュメントは基本的な機能のみを説明しています！

`integrator = init(prob::ODEProblem, alg; kwargs...)` を使用して初期化します。受け入れられるキーワード引数は、`solve` で使用されるのと同じ [共通のソルバーオプション](https://diffeq.sciml.ai/latest/basics/common_solver_opts/) です。

参考のため、`ODEIntegrator` の関連フィールドは次のとおりです：

  * `t` - 提案されたステップの時間
  * `u` - 提案されたステップの値
  * `opts` - 共通のソルバーオプション
  * `alg` - 解に関連付けられたアルゴリズム
  * `f` - 解かれている関数
  * `sol` - 解の現在の状態
  * `tprev` - 最後の時間点
  * `uprev` - 最後の時間点での値

`opts` はすべての共通のソルバーオプションを保持し、ソルバーの特性を変更するために変更できます。たとえば、将来のタイムステップの絶対許容誤差を変更するには、次のようにします：

```julia
integrator.opts.abstol = 1e-9
```

詳細については、リンクされたドキュメントページを参照してください。
