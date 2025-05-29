```
readdata(datdir::String,fname::String,n::Tuple{<:Int64,<:Int64},pexy::Tuple{<:Float64,<:Float64})
```

与えられたディレクトリ `datdir` とファイル名 `fname` から .h5 ファイルの波面分布データ（表面標高 η とその x および y における偏導関数 ηx と ηy）を読み込みます。
