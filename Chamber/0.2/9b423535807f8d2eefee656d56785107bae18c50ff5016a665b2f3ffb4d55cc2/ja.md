```
dX_dxdydz(composition::Union{Silicic,Mafic}, s::String, x::T, y::T, z::T)::NamedTuple{(:X, :dXdx, :dXdy, :dXdz),NTuple{4,T}} where {T<:Float64}
```

  * この関数は `parameters_melting_curve` 関数内で使用されます。
  * 異なるパラメータセットから値を計算します（パラメータセットの数: Silicic: 3, Mafic: 2）

## 引数

  * `composition`: `Silicic()` または `Mafic()`
  * `s`: 使用するパラメータセットを表す文字列。`Silicic` の場合、`s` は `"a"`、`"b"`、または `"c"` であることができます。`Mafic` の場合、`s` は `"a"` または `"b"` であることができます。
  * `x`: 水 (H2O)
  * `y`: ガス (CO2)
  * `z`: 圧力 (P)

## 戻り値

以下のフィールドを持つ NamedTuple:

  * `X`: 指定されたパラメータセットの計算された値
  * `dXdx`: `x` に関する `X` の導関数
  * `dXdy`: `y` に関する `X` の導関数
  * `dXdz`: `z` に関する `X` の導関数
