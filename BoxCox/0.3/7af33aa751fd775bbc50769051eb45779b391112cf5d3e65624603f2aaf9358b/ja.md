```
boxcoxplot(bc::PowerTransformation; kwargs...)
boxcoxplot!(axis::Axis, bc::PowerTransformation;
            λ=nothing, n_steps=21, xlabel="λ", ylabel="log likelihood",
            conf_level=nothing, attributes...)
```

Box-Cox変換の診断プロットを作成します。

`Axis`の変更メソッドは（修正された）元の`Axis`を返します。非変更メソッドは`Figure`を返します。

もしλが`nothing`の場合、λパラメータの可能な値の範囲は自動的に決定され、合計で`n_steps`になります。もし`λ`が数のベクトルであれば、λパラメータはそのベクトルの各要素で評価されます。

もし`conf_level`が`nothing`の場合、信頼区間は表示されません。

`attributes`は`scatterlines!`に転送されます。

!!! note
    意味のあるプロットは、`bc`が`empty!`されていない場合にのみ可能です。


!!! note
    プロット機能インターフェースはパッケージ拡張として定義されており、Makieが利用可能な場合にのみロードされます。実際にプロットをレンダリングするには、適切なMakieバックエンド（例：CairoMakieまたはGLMakie）をロードする必要があります。

