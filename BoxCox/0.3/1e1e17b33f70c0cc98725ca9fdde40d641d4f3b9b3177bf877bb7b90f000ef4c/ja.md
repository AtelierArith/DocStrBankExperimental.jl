```
YeoJohnsonTransformation <: PowerTransformation
```

# フィールド

  * `λ`: 変換パラメータ
  * `y`: 元の応答
  * `X`: 条件付き分布のモデル行列、または無条件分布の場合は `Nothing`
  * `atol`: λをゼロまたは二と比較するための許容誤差。デフォルトは1e-8

!!! note
    すべてのフィールドは内部的なものであり、実装の詳細であり、破壊的変更と見なされることなくいつでも変更される可能性があります。


# ヒント

  * λパラメータを抽出するには、`params`を使用します。
  * 変換は呼び出し可能であり、次のように実行できます。

```@example
yj = fit(YeoJohnsonTransformation, y)
y_transformed = yj.(y)
```

  * `empty!`を使用することで、メモリ内のYeoJohnsonTransformationのサイズを減らすことができますが、特定の診断（例：プロットや対数尤度の計算）は利用できなくなります。
