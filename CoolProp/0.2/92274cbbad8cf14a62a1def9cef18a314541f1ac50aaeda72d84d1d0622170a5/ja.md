```
AbstractState_set_cubic_alpha_C(handle::Clong, i::Integer, parameter::AbstractString, c1::Real, c2::Real, c3::Real)
```

立方体のアルファ関数パラメータを設定します。

# 引数

  * `handle`: メモリに保存されている状態クラスの整数ハンドル
  * `i`: パラメータを適用すべき流体のインデックス（混合物の場合）
  * `parameter`: 使用するアルファ関数を指定する文字列、例えば "TWU" はTwu、または "MC" はMathias-Copemanアルファ関数を示します。
  * `c1`: アルファ関数の最初のパラメータ
  * `c2`: アルファ関数の2番目のパラメータ
  * `c3`: アルファ関数の3番目のパラメータ
