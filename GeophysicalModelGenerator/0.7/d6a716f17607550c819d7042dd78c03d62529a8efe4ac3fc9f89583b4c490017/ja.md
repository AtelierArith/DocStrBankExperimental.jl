```
download_data(url::String, local_filename="temp.dat"; dir=pwd(), maxattempts=5 )
```

リモートのデータセットを `url` という名前でリモートの場所からダウンロードし、現在のディレクトリに保存します。ダウンロードが失敗した場合、あきらめる前に `maxattempts` 回の試行を行います。

# 例

```julia
julia> url  = "https://seafile.rlp.net/f/10f867e410bb4d95b3fe/?dl=1";
julia> download_data(url)
"/Users/kausb/.julia/dev/GeophysicalModelGenerator/temp.dat"
```
