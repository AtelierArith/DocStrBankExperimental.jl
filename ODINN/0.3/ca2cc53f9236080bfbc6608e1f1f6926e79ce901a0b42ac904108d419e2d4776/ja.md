```
SIA2D_D_target(; interpolation=:None, n_interp_half=20,
                 prescale=nothing, postscale=nothing)
```

物理パラメータの関数としての一般的な拡散率の逆算。

D(H, ∇S, θ) = H * NN(H, ∇S; θ)

したがって、今私たちはD * ∇Sによって与えられる速度場を学んでいます。この逆算は、これが表面の勾配∇Sに平行であると仮定して速度場を学ぶことに似ています。

# 引数

  * `interpolation::Symbol = :None`: 補間方法を指定します。オプションには`:Linear`、`:None`が含まれます。
  * `n_interp_half::Int = 20`: 補間ステンシルの半幅。補間の解像度を決定します。
  * `prescale::Union{Fin, Nothing} = nothing`: パラメータ化の前に適用されるオプションの前スケーリング関数または因子。`Fin`型または`nothing`でなければなりません。
  * `postscale::Union{Fout, Nothing} = nothing`: パラメータ化の後に適用されるオプションの後スケーリング関数または因子。`Fout`型または`nothing`でなければなりません。

# 型パラメータ

  * `Fin`: 前スケール関数または演算子の型。
  * `Fout`: 後スケール関数または演算子の型。

# スーパタイプ

  * `AbstractSIA2DTarget`: 2D SIAモデリングのための抽象ターゲット型から継承します。

# 戻り値

  * オプションのスケーリングおよび補間パラメータで構成された`SIA2D_D_target`のインスタンス。
