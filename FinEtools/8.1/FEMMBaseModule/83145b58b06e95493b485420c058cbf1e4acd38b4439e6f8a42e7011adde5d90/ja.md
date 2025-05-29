```
integratefieldfunction(
    self::AbstractFEMM,
    geom::NodalField{GFT},
    afield::FL,
    fh::F;
    initial::R,
    m = -1,
) where {GFT, T, FL<:NodalField{T}, F<:Function,R}
```

離散多様体上でノード場関数を統合します。

  * `afield` = ノードでの値を供給するNODALフィールドで、これはガウス点に補間されます。
  * `fh` = 位置と要素のフィールド値の配列を引数として受け取り、型`R`の値を返す関数です。関数`fh`は2つの引数を取る必要があります。`x`は位置で、`val`はその位置でのフィールドの値です。フィールド値の長方形配列`val`は1行で、ノードごとの自由度の数だけ列があります。
  * `m` = 統合する多様体の次元; `m < 0`は、次元が要素の多様体次元によって制御されることを意味します。

型`R`のスカラー値を返す関数を統合し、これは`initial`によって初期化されます。
