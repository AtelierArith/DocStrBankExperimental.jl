ACSetsとLooseACSetTransformationsの図の限界。

一般的な図形の形状において、カテゴリ的な限界の頂点はその属性に対してクリーンなJulia型を持たないため、さらなる制約を加えるために述語が必要になります。述語が必要な場合にエラーを回避するために、`product_attrs`をオンにする必要があります。

`product_attrs=true`は、純粋に組み合わせ的なデータの限界を取り、頂点の属性データは明示的な円錐脚を持つACSetsによって純粋に決定されます。頂点のi番目の部分に対する属性の値（例：`f`）は、`(f(π₁(i)), ..., f(πₙ(i)))`という積であり、ここでπは限界脚の組み合わせ的部分から来るマッピングです。限界のj番目の脚の型コンポーネントは、単にj番目のデカルト射影です。
