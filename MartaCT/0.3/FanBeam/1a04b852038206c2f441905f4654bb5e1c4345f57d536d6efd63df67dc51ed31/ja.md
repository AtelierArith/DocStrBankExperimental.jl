```
fan2para(
    sinog_fan::AbstractMatrix{T},
    fbg::FanBeamGeometry;
    <keyword arguments>
) where {T} -> pbg, sinog_para
```

与えられたシノグラム `sinog_fan` をファンビーム幾何学から平行ビーム投影に変換します。

検出器は平坦ではなく、円弧上に配置されていると仮定します。

この関数は、`fbg` がファンビーム投影パラメータを持つ新しい幾何学であり、`sinog_fan` が変換されたシノグラムであるタプルを返します。

# 引数

  * `sinog_para`: 入力シノグラム。
  * `pbg`: 平行幾何学パラメータ。
  * `background=nothing`: 使用される背景値、デフォルトは0。
  * `interpolation`: 補間戦略; 行列を入力として受け取り、補間値を取得するためのインデックスの関数を返す関数である必要があります。デフォルトではバイリニア補間です。

関連: [`para2fan`](@ref)
