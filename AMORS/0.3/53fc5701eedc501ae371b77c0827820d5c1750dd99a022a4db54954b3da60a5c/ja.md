```
info = AMORS.Info(α, Gxy, μ, Jx, q, ν, Ky, r, iter, eval, status)
```

は、AMORSアルゴリズムの状態に関するすべての情報を格納する構造化されたオブジェクトを構築します。この種のオブジェクトは[`AMORS.solve`](@ref)および[`AMORS.solve!`](@ref)によって返されます。

オブジェクトのプロパティには、コンストラクタの引数が含まれます：

```
info.α         # スケーリングファクター
info.Gxy       # G(x⊗y)の値
info.μ         # J(x)のハイパーパラメータの値
info.J         # J(x)の値
info.q         # J(x)の同次次数
info.ν         # K(y)のハイパーパラメータの値
info.Ky        # K(y)の値
info.r         # K(y)の同次次数
info.autoscale # 最適なスケーリングファクターを自動的に取得するか？
info.iter      # イテレーションの数
info.eval      # "評価"の数
info.status    # アルゴリズムの現在の状態
```

さらにいくつかのプロパティがあります：

```
info.αbest  # 最適なスケーリングファクター
info.Fxy    # F(α*x, y/α, μ, ν)の値
info.η      # 効果的なハイパーパラメータ
```

ここで、`F(x,y,μ,ν) = G(x⊗y) + μ*J(x) + ν*K(y)`はAMORSアルゴリズムによって最小化される目的関数です。`info.αbest`と`info.α`は、[`AMORS.solve`](@ref)または[`AMORS.solve!`](@ref)で自動スケーリングが無効になっている場合、異なる可能性があることに注意してください。
