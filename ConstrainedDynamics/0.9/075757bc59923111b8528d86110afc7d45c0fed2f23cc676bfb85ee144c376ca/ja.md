```julia
abstract type Controller
```

ユーザーは `Controller` のサブタイプを作成してコントローラーを実装できます。そのようなコントローラーオブジェクトが `simulate!` に渡されると、各タイムステップで `controller.control!(mechanism, controller, timestep)` が呼び出されます。この方法で、ユーザーは `mechanism`、`controller`、およびタイムステップのすべての属性にアクセスできます。制御関数は `control!` と呼ばれる必要があることに注意してください。
