```
get_solidangle(x, [y=0; angunit=u"rad", angunitout=nothing, satype="pixel"])
```

指定された単位での角サイズのセットに対して固体角を計算します。

# 引数

  * `Δx, Δy::Real`:   2つの直交方向における面積のサイズ。`Δy <= 0` の場合、`Δy = Δx` となります。
  * `angunit::Unitful.Units or Unitful.Quantity`:   `Δx` と `Δy` の角度単位。デフォルトは `rad` です。
  * `angunitout::Unitful.Units, Unitful.Quantity or nothing`:    出力固体角の角度単位。何も指定されていない場合は、`angunit` で指定されたのと同じ単位を使用します。
  * `satype::Symbol`   出力固体角のタイプ：   矩形面積の固体角には `:pixel` を、ビーム固体角には `:beam` を使用します。   `:beam` の場合、Δx, Δy はガウスFWHMとして解釈されます。
