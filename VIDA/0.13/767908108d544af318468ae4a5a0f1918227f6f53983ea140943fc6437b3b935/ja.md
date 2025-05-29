```julia
divergence(d, m)

```

`d`に対するテンプレート`m`に関する発散を計算します。この測定は、`d`に保存された画像に対する発散がテンプレートにどれだけ類似しているかを示します。

# 引数

  * `d`: 発散または[`VIDA.AbstractDivergence`](@ref)のサブタイプ
  * `m`: `ComradeBase.AbstractModel`またはより一般的には[`VIDA.AbstractImageTemplate`](@ref)であるテンプレート
