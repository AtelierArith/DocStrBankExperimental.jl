```
ScienceBase <: DataSource
```

[Lidar Point Cloud (LPC)](https://www.sciencebase.gov/catalog/item/4f70ab64e4b058caae3f8def) データセットは、[United States Geological Survey (USGS)](https://www.usgs.gov/) の[ScienceBaseカタログ](https://www.sciencebase.gov/catalog/)にあります。このデータセットには、[USGS 3D Elevation Program (3DEP)](https://www.usgs.gov/3d-elevation-program)の一環として生成された生のポイントクラウドデータが含まれており、アメリカ合衆国全体のカバレッジに近づいています。

[USGSのウェブサイト](https://www.usgs.gov/3d-elevation-program)によると、「すべての3DEP製品は無料で利用でき、使用制限はありません」（参照: [The National Mapの利用規約](https://www.usgs.gov/faqs/what-are-terms-uselicensing-map-services-and-data-national-map)）。ただし、[ScienceBaseユーザー契約](https://www.sciencebase.gov/catalog/UserAgreement/show)では、APIユーザーに「ウェブの慣習に従った責任ある使用の実践を守るように」と求めています。

このタイプを[`gettiles`](@ref)関数に渡して、`ScienceBase`データセットをクエリします。[クエリの指示](https://www.usgs.gov/sciencebase-instructions-and-documentation/building-search-queries)によれば、各クエリは最大1000アイテムを返すことができます。また、`ScienceBase(id)`を使用して特定のScienceBaseアイテムの`PointCloudTile`を取得することもできます。ここで、`id`はScienceBaseのURLから取得できます。
