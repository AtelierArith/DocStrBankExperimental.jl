```
ScienceBase <: DataSource
```

[Lidar Point Cloud (LPC)](https://www.sciencebase.gov/catalog/item/4f70ab64e4b058caae3f8def) dataset in the [ScienceBase catalog](https://www.sciencebase.gov/catalog/) of the [United States Geological Survey (USGS)](https://www.usgs.gov/). This dataset contains raw point-cloud data produced as part of the [USGS 3D Elevation Program (3DEP)](https://www.usgs.gov/3d-elevation-program), which is approaching nationwide coverage of the United States.

According to the [USGS website](https://www.usgs.gov/3d-elevation-program), “all 3DEP products are available free of charge and without use restrictions” (see also: [Terms of Use for The National Map](https://www.usgs.gov/faqs/what-are-terms-uselicensing-map-services-and-data-national-map)). Note however that the [ScienceBase User Agreement](https://www.sciencebase.gov/catalog/UserAgreement/show) asks API users “to adhere to practices of responsible use in accordance to web convention”.

Pass this type to the [`gettiles`](@ref) function to query the `ScienceBase` dataset. As per [the query instructions](https://www.usgs.gov/sciencebase-instructions-and-documentation/building-search-queries), each query can return a maximum of 1000 items. You can also obtain the `PointCloudTile` of a specific ScienceBase item with `ScienceBase(id)`, where the `id` can be obtained e.g. from the ScienceBase URL.
