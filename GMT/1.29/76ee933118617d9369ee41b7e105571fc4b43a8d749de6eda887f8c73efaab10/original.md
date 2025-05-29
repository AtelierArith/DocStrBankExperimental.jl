```
D = mat2ds(mat::Array{T,N}, D::GMTdataset)
```

Take a 2D `mat` array and convert it into a GMTdataset. Pass in a reference GMTdataset from which we'll take the georeference info as well as `attrib` and `colnames`.
