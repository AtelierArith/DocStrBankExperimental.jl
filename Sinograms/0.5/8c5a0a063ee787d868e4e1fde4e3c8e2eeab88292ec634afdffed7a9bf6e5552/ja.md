```
SinoFanFlat( ; nb d offset na orbit orbit_start
    source_offset, dsd= 4 * nb * d, dod = nb * d)
SinoFanFlat(:short ; ...)
```

名前付きキーワードを持つコンストラクタ。ドキュメントについては `?SinoGeom` を参照してください。

  * `:short` 引数を使用して短いスキャンを指定します。この場合、`na` も比例して縮小されます。

```jldoctest
julia> SinoFanFlat()
SinoFanFlat{Float32, Float32} :
 nb::Int64 128
 d::Float32 1.0
 offset::Float32 0.0
 na::Int64 200
 orbit::Float32 360.0
 orbit_start::Float32 0.0
 source_offset::Float32 0.0
 dsd::Float32 512.0
 dod::Float32 128.0
```
