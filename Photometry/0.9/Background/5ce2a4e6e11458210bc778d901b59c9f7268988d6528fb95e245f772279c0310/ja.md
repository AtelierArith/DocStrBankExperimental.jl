```
estimate_background(data;
    location=SourceExtractorBackground(),
    rms=StdRMS(),
    dims=:)
```

与えられた推定器を使用してスカラー背景推定を行います。

返される値は、推定された背景と推定された背景RMSに対応する2つの値になります。次元性は`dims`キーワードに依存します。

`location`と`rms`は、例えば`median`のように呼び出し可能なものであれば何でも構いません。また、[Background Estimators](@ref)で提供する推定器の1つでも構いません。

# 例

```jldoctest
julia> data = ones(3, 5);

julia> bkg, bkg_rms = estimate_background(data)
(1.0, 0.0)

julia> using Statistics: median

julia> bkg, bkg_rms = estimate_background(data; location=median, rms=MADStdRMS())
(1.0, 0.0)
```

# 参照

  * [Location Estimators](@ref), [RMS Estimators](@ref)
