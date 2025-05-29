```
D = mat2ds(mat::Array{T,N}, D::GMTdataset)
```

2Dの`mat`配列を取得し、GMTdatasetに変換します。ジオリファレンス情報、`attrib`、および`colnames`を取得するために、参照GMTdatasetを渡します。
