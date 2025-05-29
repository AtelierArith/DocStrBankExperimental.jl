```
obj = pelvis_phantom2D(; ss=4, us=1)
```

2次元骨盤ファントム構造体を作成します。デフォルトのss=4サンプル間隔は2 mmです。元のファイル（ss=1）のサンプル間隔は0.5 mmです。

# キーワード

  * `ss`: (`::Integer or ::Vector{Integer}`, `=4`) スカラーの場合はすべての軸のサブサンプリングパラメータ、2要素ベクトル[ssx, ssy]の場合は各軸のサブサンプリングパラメータ
  * `us`: (`::Integer or ::Vector{Integer}`, `=1`) スカラーの場合はすべての軸のアップサンプリングパラメータ、2要素ベクトル[usx, usy]の場合は各軸のアップサンプリングパラメータ

# 戻り値

  * `obj`: (`::Phantom`) ファントム構造体

# 例

```julia-repl
julia> obj = pelvis_phantom2D(; ss=2)

julia> obj = pelvis_phantom2D(; us=[1, 2])

julia> pelvis_phantom2D(obj, :ρ)
```
