```
CMINPACK(; method::Symbol = :auto, autodiff = missing)
```

### キーワード引数

  * `method`: ソルバーのためのメソッドの選択。
  * `autodiff`: デフォルトは `missing` で、これは `f.jac` が提供されていない場合に `MINPACK` によってヤコビアンを構築させることを意味します。他の場合では、他の NonlinearSolve ソルバーと同様にヤコビアンを生成するために使用します。

### サブメソッドの選択

キーワード引数 `method` は、呼び出している `fsolve` のメソッドに応じて異なる値を取ることができます。`method` の標準的な選択肢は次のとおりです：

  * `:hybr`: パウエルのアルゴリズムの修正版。MINPACK ルーチン [`hybrd1`](https://github.com/devernay/cminpack/blob/d1f5f5a273862ca1bbcf58394e4ac060d9e22c76/hybrd1.c) を使用します。
  * `:lm`: レーベンバーグ-マルカート。MINPACK ルーチン [`lmdif1`](https://github.com/devernay/cminpack/blob/d1f5f5a273862ca1bbcf58394e4ac060d9e22c76/lmdif1.c) を使用します。
  * `:lmdif`: 高度なレーベンバーグ-マルカート（`; kwargs...` でより多くのオプションが利用可能）。詳細については MINPACK ルーチン [`lmdif`](https://github.com/devernay/cminpack/blob/d1f5f5a273862ca1bbcf58394e4ac060d9e22c76/lmdif.c) を参照してください。
  * `:hybrd`: パウエルのアルゴリズムの高度な修正版（`; kwargs...` でより多くのオプションが利用可能）。詳細については MINPACK ルーチン [`hybrd`](https://github.com/devernay/cminpack/blob/d1f5f5a273862ca1bbcf58394e4ac060d9e22c76/hybrd.c) を参照してください。

[`NonlinearFunction`](@ref nonlinearfunctions) の一部としてヤコビアンが提供されている場合、次のメソッドが許可されます：

  * `:hybr`: ユーザー提供のヤコビアンを持つパウエルのアルゴリズムの高度な修正版。追加の引数は `; kwargs...` を介して利用可能です。詳細については MINPACK ルーチン [`hybrj`](https://github.com/devernay/cminpack/blob/d1f5f5a273862ca1bbcf58394e4ac060d9e22c76/hybrj.c) を参照してください。
  * `:lm`: ユーザー提供のヤコビアンを持つ高度なレーベンバーグ-マルカート。追加の引数は `; kwargs...` を介して利用可能です。詳細については MINPACK ルーチン [`lmder`](https://github.com/devernay/cminpack/blob/d1f5f5a273862ca1bbcf58394e4ac060d9e22c76/lmder.c) を参照してください。

デフォルトの選択肢 `:auto` は、NonlinearProblem に対して `:hybr` を、NonlinearLeastSquaresProblem に対して `:lm` を選択します。

!!! note
    このアルゴリズムは `MINPACK.jl` がインストールされ、ロードされている場合にのみ利用可能です。

