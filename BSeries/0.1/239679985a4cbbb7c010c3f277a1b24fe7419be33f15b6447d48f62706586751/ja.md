```
bseries(ark::AdditiveRungeKuttaMethod, order)
```

加法ルンゲクッタ法 `ark` のB系列を指定された整数 `order` まで計算します。

!!! note "基本微分による正規化"
    このメソッドによって返されるB系列の係数は、時間ステップのべき乗を色付き根付き木の `symmetry` で割り、入力ベクトル場 $f^\nu$ の対応する基本微分で掛ける必要があります。詳細は [`evaluate`](@ref) を参照してください。

