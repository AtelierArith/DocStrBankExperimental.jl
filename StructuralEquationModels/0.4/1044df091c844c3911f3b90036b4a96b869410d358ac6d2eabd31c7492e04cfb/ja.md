```
fit([optim::SemOptimizer], model::AbstractSem;
        [engine::Symbol], start_val = start_val, kwargs...)
```

適合した `model` を返します。

# 引数

  * `optim`: [`SemOptimizer`](@ref) を使用して適合させます。省略した場合、新しいオプティマイザが `SemOptimizer(; engine, kwargs...)` として構築されます。
  * `model`: 適合させる `AbstractSem`
  * `engine`: 使用する最適化エンジン、デフォルトは `:Optim`
  * `start_val`: 開始パラメータ値のベクトルまたは辞書、またはそれらを計算する関数 (1)
  * `kwargs...`: 最適化エンジンコンストラクタおよび `start_val` 関数に渡されるキーワード引数

(1) 利用可能な関数は `start_fabin3`、`start_simple` および `start_partable` です。詳細については、個別のドキュメントおよび [Starting values](@ref) に関するオンラインドキュメントを参照してください。

# 例

```julia
fit(my_model;
    start_val = start_simple,
    start_covariances_latent = 0.5)
```

```julia
using Optim

fit(my_model;
    algorithm = BFGS())
```
