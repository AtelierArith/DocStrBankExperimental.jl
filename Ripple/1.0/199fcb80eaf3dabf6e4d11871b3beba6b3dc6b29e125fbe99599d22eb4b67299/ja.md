```
function read_nfx(fname::String; applygain=true)
```

NFxファイル`fname`を読み込み、[`NxFile`](@ref)を返します。

`applygain`が`true`の場合、計算されたゲインとオフセットをデータに自動的に適用します。
