```
integratefieldfunction(
    self::AbstractFEMM,
    geom::NodalField{GFT},
    afield::FL,
    fh::F;
    initial::R = zero(FT),
    m = -1,
) where {GFT, T, FL<:ElementalField{T}, F<:Function,R}
```

離散多様体上での要素場関数を統合します。

  * `afield` = 要素内で値を供給する要素場（要素ごとに1つの値）、
  * `fh` = 位置と要素のフィールド値の配列を引数として受け取り、型 `R` の値を返す関数。関数 `fh` は2つの引数を取る必要があります。`x` は位置、`val` はその位置でのフィールドの値です。フィールド値の長方形配列 `val` は1行で、ノードごとの自由度の数だけ列があります。
  * `m` = 統合する多様体の次元；`m < 0` は、次元が要素の多様体次元によって制御されることを意味します。

型 `R` のスカラー値を返す関数を統合し、これは `initial` によって初期化されます。
