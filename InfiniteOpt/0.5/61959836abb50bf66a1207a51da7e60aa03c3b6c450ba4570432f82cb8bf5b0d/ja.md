```
RegisteredFunction{F <: Function, G <: Union{Function, Nothing}, 
                   H <: Union{Function, Nothing}}
```

JuMPが`NLPEvaluator`を構築するために必要な、ユーザー定義の登録関数とその情報を格納するための型です。コンストラクタは次の形式です：

```julia
    RegisteredFunction(name::Symbol, num_args::Int, func::Function, 
                       [gradient::Function, hessian::Function])
```

**フィールド**

  * `name::Symbol`: `NLPExpr`で使用される関数の名前。
  * `num_args::Int`: 関数引数の数。
  * `func::F`: 関数自体。
  * `gradient::G`: 与えられた場合の勾配関数。
  * `hessian::H`: 与えられた場合のヘッセ行列関数。
