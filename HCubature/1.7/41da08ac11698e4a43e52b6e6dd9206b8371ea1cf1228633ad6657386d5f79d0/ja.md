```
hquadrature(f, a, b; norm=norm, rtol=sqrt(eps), atol=0, maxevals=typemax(Int), initdiv=1)
```

`f(x)`の`a`から`b`までの積分を計算します。`hcubature`の戻り値は、推定された積分`I`と推定誤差`E`のタプル`(I, E)`です。

他のパラメータは[`hcubature`](@ref)と同じです。`hquadrature`は、スカラー`x`、`a`、および`b`を扱うための便利なラッパーです。1成分のベクトルではなく。

また、1次元の積分の場合は、[`QuadGK`](@ref)モジュールをインポートし、四分法の順序を選択するなどの追加の柔軟性を提供する[`quadgk`](@ref)関数を呼び出すことができます。
