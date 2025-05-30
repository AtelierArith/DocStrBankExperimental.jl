```
BoxCoxTransformation <: PowerTransformation
```

# フィールド

  * `λ`: 変換パラメータ
  * `y`: 幾何平均で正規化された元の応答
  * `X`: 条件付き分布のためのモデル行列、または無条件分布のための`Nothing`
  * `atol`: λをゼロと比較するための許容誤差。デフォルトは1e-8

!!! note
    すべてのフィールドは内部的なものであり、実装の詳細であり、破壊的変更と見なされることなくいつでも変更される可能性があります。


# ヒント

  * λパラメータを抽出するには、`params`を使用します。
  * 変換は呼び出し可能であり、次のように行うことができます。

```@example
bc = fit(BoxCoxTransformation, y)
y_transformed = bc.(y)
```

  * `empty!`を使用することで、メモリ内のBoxCoxTransformationのサイズを減らすことができますが、特定の診断（例：プロットや対数尤度の計算）はもはや利用できなくなります。

さらに[`boxcoxplot`](@ref)、[`params`](@ref)、[`boxcox`](@ref)を参照してください。
