```
area_closing(image, [maxtree]; min_area=64, connectivity=1) -> Array
```

`image`の*エリアクローズ*を実行します。

*エリアクローズ*は、`min_area`より小さい面積を持つ画像のすべての暗い成分を、`image`の*マックスツリー*表現において、`min_area`以上の面積を持つ最初の祖先成分から取得した明るい値で置き換えます。

# 詳細

*エリアクローズ*は*エリアオープン*の双対操作です（[`area_opening`](@ref)を参照）。これは形態学的クローズ（[`closing`](@ref)を参照）に似ていますが、固定の構造要素（例：ディスク）を使用するのではなく、*マックスツリー*の小さな（`min_area`未満の）成分を使用します。したがって、`min_area = 1`の`area_closing`は恒等変換です。

バイナリの場合、エリアクローズは`remove_small_holes`に相当します。この演算子はグレーレベル画像にも拡張されます。

# 引数

  * `image::GenericGrayImage`: $N$次元の入力画像
  * `min_area::Number=64`: そのまま保持する画像成分の最小サイズ（ピクセル単位）
  * `connectivity::Integer=1`: 隣接接続性。ピクセルの隣接者に到達するための最大直交ステップ数。2Dでは、4近傍の場合は1、8近傍の場合は2です。
  * `maxtree::MaxTree`: オプションの事前構築された*マックスツリー*。`maxtree`と`connectivity`のオプションパラメータは相互に排他的であることに注意してください。

# 戻り値

`image`と同じ型と形状の配列。

# 参照

[`area_closing!`](@ref), [`area_opening`](@ref), [`diameter_closing`](@ref), [`MaxTree`](@ref), [`closing`](@ref)

# 参考文献

1. Vincent, L. (1993). *グレースケールエリアオープンとクローズ、その効率的な実装と応用*, Proc. of EURASIP Workshop on Mathematical Morphology and its Applications to Signal Processing, Barcelona, Spain, 22-27
2. Soille, P. (2003). Chapter 6 *測地的メトリック* of *形態学的画像分析：原則と応用*, 第2版, Springer.

    > https://doi.org/10.1007/978-3-662-05088-0
3. Salembier, P., Oliveras, A., & Garrido, L. (1998). *画像とシーケンス処理のための反拡張接続演算子*. IEEE Transactions on Image Processing, 7(4), 555-570.

    > https://doi.org/10.1109/83.663500
4. Najman, L., & Couprie, M. (2006). *準線形時間での成分ツリーの構築*. IEEE Transactions on Image Processing, 15(11), 3531-3539.

    > https://doi.org/10.1109/TIP.2006.877518
5. Carlinet, E., & Geraud, T. (2014). *成分ツリー計算アルゴリズムの比較レビュー*. IEEE Transactions on Image Processing, 23(9), 3885-3895.

    > https://doi.org/10.1109/TIP.2014.2336551

# 例

テスト画像`f`を作成します（中心に最小値があり、4つの追加の局所最小値を持つ二次関数）：

```jldoctest; setup = :(using ImageMorphology)
julia> w = 12;

julia> f = [180 + 0.2*((x - w/2)^2 + (y-w/2)^2) for x in 0:w, y in 0:w];

julia> f[3:4, 2:6] .= 40; f[3:5, 10:12] .= 60; f[10:12, 3:5] .= 80;

julia> f[10:11, 10:12] .= 100; f[11, 11] = 100;

julia> f_aclose = area_closing(f, min_area=8, connectivity=1);
```

すべての小さな最小値が削除され、残りの最小値は少なくとも8のサイズを持っています。 ```
