```
bezigon(corners::Vector{Point}, sides;
    close = false,
    action = :none))
```

ベジゴンを構築します。これは、ベジエ曲線で構成されたパスです。

`corners` は、ベジゴンのコーナーである点の配列です。例えば、この三角形：

```julia
[Point(0, 0), Point(50, 50), Point(100, 0)]
```

`sides` は、各配列が2つの制御点を含む点の配列の配列です。例えば：

```julia
sides = [
    [Point(-10, -20), Point(40, -120)], # 最初の辺の制御点
    [Point(120, -120), Point(180, -20)],
]
```

最初のペアの `sides`（2つの点）は制御点であり、最初の2つの `corners` の点と組み合わさってベジエ曲線を定義します。次のペアについても同様です。

パスを返します。
