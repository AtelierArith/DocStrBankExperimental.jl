```
load_GMG(filename::String, dir=pwd(); maxattempts=5)
```

`filename`から`GeoData`/`CartData`/`UTMData`データセットをjld2ファイルから読み込みます。注意: `filename`はリモート`url`でも可能で、その場合は最初にそのファイルを一時ディレクトリにダウンロードしてから開きます。ダウンロードするために`maxattempts`回の試行を行い、諦めます。

# 例 1 - ローカルファイルの読み込み

```julia
julia> data = load_GMG("test")
GeoData 
  size      : (4, 3, 3)
  lon       ϵ [ 1.0 : 10.0]
  lat       ϵ [ 11.0 : 19.0]
  depth     ϵ [ -20.0 : -10.0]
  fields    : (:DataFieldName,)
  attributes: ["note"]
```

# 例 2 - リモートダウンロード

```julia
julia> url  = "https://seafile.rlp.net/f/10f867e410bb4d95b3fe/?dl=1"
julia> load_GMG(url)
GeoData 
  size      : (149, 242, 1)
  lon       ϵ [ -24.875 : 35.375]
  lat       ϵ [ 34.375 : 71.375]
  depth     ϵ [ -11.76 : -34.7]
  fields    : (:MohoDepth,)
  attributes: ["author", "year"]
```
