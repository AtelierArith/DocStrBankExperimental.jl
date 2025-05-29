```
AbstractState_set_fluid_parameter_double(handle::Clong, i::Integer, parameter::AbstractString, value::Real)
```

流体パラメータ（すなわち立方体の体積変換）を設定します。現在は、成分ではなく全体の流体に適用されています。

# 引数

  * `handle`: メモリに保存されている状態クラスの整数ハンドル
  * `i`: パラメータを適用すべき流体のインデックス（混合物の場合）
  * `parameter`: パラメータの名前を含む文字列、例えば体積変換パラメータのための "c", "cm", "c_m" など。
  * `value`: パラメータの値
