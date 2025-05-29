```
PNSystem{ST, PNOrder}
```

すべてのPNシステムの基本型であり、`BBH`、`BHNS`、および`NSNS`などがあります。

これらのオブジェクトは、バイナリの現在の状態を含むすべての重要な特性をエンコードします。そのため、さまざまな[基本的な](@ref Fundamental-variables)および[導出変数](@ref Derived-variables)、さらに[PN式](@ref)や[ダイナミクス](@ref Dynamics)関数への入力として使用できます。

すべてのサブタイプは、指定されたタイプのシステムに対するすべての基本変数を保持する`state`ベクトルを含む必要があります。パラメータ`ST`は`state`ベクトルの型であり、例えば`Vector{Float64}`です。`PNOrder`は、PN展開が行われるべき次数を与える`Rational`です。
