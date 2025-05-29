```
geoEff(detector::Detector, aPnt::Point, SrcRadius::Real = 0.0, SrcLength::Real = 0.0)::Float64
```

検出器 `detector` に対するソース（`point`、`disk` または `cylinder`）の `geometrical efficiency` を返します。

## 引数

  * `detector` は任意のリーフ検出器タイプ（`CylDetector`、`BoreDetector`、`WellDetector`）であることができます。
  * `aPNT`: ソースのアンカーポイントを表す点。
  * `SrcRadius`: ソースの半径。
  * `srcHeight`: 立っている円柱ソースの高さ。

## 例外

  * 点の位置が無効な場合は `InValidGeometry` をスローします。
  * ソースから検出器の幾何学がまだサポートされていない場合は `NotImplementedError` をスローします。

!!! 警告     `aPnt` の点の高さは、異なる検出器タイプによって異なる方法で測定されます。詳細については、各検出器のエントリを参照してください。

!!! 注       * `SrcLength` が `zero` に等しい場合、メソッドは半径 `SrcRadius` の円盤ソースの幾何学的効率を返し、中心は点 `aPNT` にあります。       * `SrcRadius` と `SrcLength` の両方が `zero` に等しい場合、メソッドはアンカーポイントでの点ソースの幾何学的効率を返します。

# 例

  * 半径 `2.0` cm の結晶の `cylindrical` 検出器の効率を、半径 `1.0` cm、高さ `2.5` cm の軸方向ソース円柱に対して、検出器の表面で取得します。

```jldoctest
julia> using GeoEfficiency

julia> geoEff(CylDetector(2.0), Point(0.0), 1.0, 2.5)
0.2923777934922748
```

  * 半径 `2.0` cm、高さ `3.0` cm の結晶の `bore-hole` 検出器の効率を、半径 `1.5` cm の穴を持つ軸方向ソース円柱（半径 `1.0` cm、高さ `2.5` cm）に対して、検出器の中心から取得します。

```jldoctest
julia> using GeoEfficiency

julia> newDet = BoreDetector(2.0, 3.0, 1.5);

julia> geoEff(newDet, Point(0.0), 1.0, 2.5)
0.5678174038944723
```

  * 半径 `2.0` cm、高さ `3.0` cm の結晶の `well-type` 検出器の効率を、半径 `1.5` cm の穴と深さ `1.0` cm を持つ軸方向ソース円柱（半径 `1.0` cm、高さ `2.5` cm）に対して、穴の表面で取得します。

```jldoctest
julia> using GeoEfficiency

julia> newDet = WellDetector(2.0, 3.0, 1.5, 1.0);

julia> geoEff(newDet, Point(0.0), 1.0, 2.5)
0.4669614527701105
```
