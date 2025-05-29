```
DP8Solver(f, x, y; kw...)
```

8次のドルマン-プリンスソルバーオブジェクトを作成して、ODE問題 `y' = f(x, y)` を解きます。

# 例

```julia
julia> fcn(x, y, f)
            f[1] = 0.85y[1]
        end

julia> solver = DP8Solver(fcn, 0.0, [19.0]; atol = 1e-10, rtol = 1e-10)
```

# 引数

  * `f`: ODEを表す関数で、`f(x, y, f)`の形式である必要があります。
  * `x`: ODE問題の開始時点。
  * `y`: ベクトル形式のODEの初期値。

# キーワード引数

  * `atol`: 絶対許容誤差。デフォルトは1e-10。
  * `rtol`: 相対許容誤差。デフォルトは1e-10。
  * `uround`: 丸め単位、デフォルトはeps(T)で、T <: Real。
  * `safety_factor`: ステップサイズ予測の安全係数、デフォルトは0.9。
  * ステップサイズ選択パラメータ、新しいステップサイズは次の制約に従います: `step_size_selection_one <= new_step/old_step <= step_size_selection_two`

      * `step_size_selection_one`: デフォルトは0.2。
      * `step_size_selection_two`: デフォルトは10.0。
  * `beta`: 安定化されたステップサイズ制御のためのベータ。大きな値のベータ (<= 0.1) はステップサイズ制御をより安定にします。
  * `maximal_step_size`: ステップサイズの最大値。デフォルトは0.0で、内部的には `xend - x` に変換されます。
  * `initial_step_size`: 初期ステップサイズ、デフォルトは0.0。初期推定値が内部的に計算されます。
  * `maximum_allowed_steps`: 許可される最大ステップ数、デフォルトは100000。
  * `print_error_messages`: エラーメッセージを表示するかどうか、デフォルトはtrue。
  * `stiffness_test_activation_step`: このステップ数の整数倍の後に、剛性検出を行います。デフォルトは1000。
