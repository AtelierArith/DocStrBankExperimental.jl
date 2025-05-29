```
function fitdipole(m::HealpixMap{T}, [w::HealpixMap{T}=1]) where T
```

マップのモノポールとダイポールをフィットします。

# 引数:

  * `m::HealpixMap{T}`: フィットするマップ
  * `w::HealpixMap{T}`: 重みマップ。デフォルトは1のFillArrayです。

# 戻り値:

  * `Tuple{T, NTuple{3,T}}`: (モノポール, (ダイポール x, ダイポール y, ダイポール z))
