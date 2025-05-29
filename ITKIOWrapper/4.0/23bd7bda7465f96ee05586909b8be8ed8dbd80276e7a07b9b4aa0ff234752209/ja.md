```
save_image(voxel_data::DataStructs.VoxelData, metadata::DataStructs.SpatialMetaData, 
          output_path::String, is_dicom::Bool=false)
```

ボクセルデータとメタデータをNIfTIファイルまたはDICOMシリーズに保存します。
