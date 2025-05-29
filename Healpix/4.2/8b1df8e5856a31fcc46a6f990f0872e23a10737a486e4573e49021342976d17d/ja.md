```
readPolarizedMapFromFITS{T}(fileName::AbstractString, column, t::Type{T})
```

FITSファイルから偏光マップ（I/Q/U）を読み込み、[`PolarizedHealpixMap`](@ref)オブジェクトを返します。

パラメータ`column`は、数値または3要素のタプルのいずれかです。最初のケースでは、`column`（1ベースのインデックス）から始まる3つの連続した列が読み込まれ、それ以外の場合は3つの列インデックスが使用されます。
