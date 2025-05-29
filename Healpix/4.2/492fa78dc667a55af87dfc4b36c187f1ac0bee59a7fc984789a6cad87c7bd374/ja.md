```
combinemaps{T, O, H}(destmap::HealpixMap{T, O}, desthitmap::HealpixMap{H, O}, othermap::HealpixMap{T, O}, otherhitmap::HealpixMap{H, O})
```

"othermap"を"destmap"に加算します。両方のマップはTODをビン分けして生成されたと仮定します。パラメータ`desthitmap`と`otherhitmap`は2つのヒットマップです。呼び出しの最後に、`destmap`と`desthitmap`が更新されます。
