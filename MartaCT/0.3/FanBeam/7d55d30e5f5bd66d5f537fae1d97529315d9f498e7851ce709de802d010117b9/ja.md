```
para2fan(
    sinog_para::AbstractMatrix{T},
    fbg::FanBeamGeometry;
    <keyword arguments>
) where {T} -> fbg, sinog_fan
```

与えられたシノグラム `sinog_para` を平行ビーム幾何学からファンビーム投影に変換します。

この関数は、`fbg` がファンビーム投影パラメータを持つ新しい幾何学であり、`sinog_fan` が変換されたシノグラムであるタプルを返します。

# 引数

  * `sinog_para`: 入力シノグラム。
  * `pbg`: 幾何学パラメータ。
  * `D`: 焦点からISOまでの距離。
  * `D′=nothing`: 焦点から検出器までの距離; 指定されていない場合、かつ `γ` が指定されていない場合、全体のファン角が1ラジアンになるように定義されます。
  * `γ=nothing`: 全体のファン角（度）。
  * `δ=1`: 検出器の間隔（セルサイズ）。
  * `background=nothing`: 使用される背景値、デフォルトは0。
  * `interpolation`: 補間戦略; 行列を入力として受け取り、補間値を取得するためのインデックスの関数を返す関数である必要があります。デフォルトではバイリニア補間です。

関連情報: [`fan2para`](@ref)
