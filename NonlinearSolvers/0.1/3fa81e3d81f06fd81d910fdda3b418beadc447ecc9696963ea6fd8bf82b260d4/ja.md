```
NewtonsMethod(
        f!::F!,
        j!::J!,
        x_init::A,
    ) where {F! <: Function, J! <: Function, A <: AbstractArray}
```

非線形方程式のシステムタイプ。

# フィールド

  * `f!`: 根を見つけるための関数
  * `j!`: `f!` のヤコビ行列
  * `x_init`: 初期推定
  * `x1`: ストレージ
  * `J`: ストレージ
  * `J⁻¹`: ストレージ
  * `F`: ストレージ
