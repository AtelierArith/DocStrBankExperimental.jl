```
body_derivatives(system, surfaces, reference, freestream; kwargs...)
```

ボディフォースとモーメントのフリーストリーム速度成分 `(u, v, w)` およびボディフレーム内の角速度成分 `(p, q, r)` に関する導関数を返します。

導関数は2つの名前付きタプル `dCF, dCM` として返されます。

パネルフォースのフリーストリーム変数に関する導関数は、事前に計算されて `system` に保存されている必要があります。

# 引数:

  * `system`: システムプロパティを保持する `System` 型のオブジェクト
