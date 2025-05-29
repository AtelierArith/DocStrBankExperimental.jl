```
exported(ed::Array{<:Real,3},η::Array{<:Real,2},p::Param,
              fname::String,mode="2D"::String,nk=0::Int64)
```

`fname`.h5ファイルに放射照度データをエクスポートしました。

データをエクスポートするモードは3つあります: `2D`、`3D`、および `full`。指定されていない場合、モードは自動的に `2D` に設定されます。
