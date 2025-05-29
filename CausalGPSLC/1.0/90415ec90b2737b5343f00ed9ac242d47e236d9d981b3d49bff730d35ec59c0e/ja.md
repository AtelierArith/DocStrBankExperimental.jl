```
saveGPSLCObject(g, filename)
saveGPSLCObject(g, "path/to/filename")
saveGPSLCObject(g, "path/to/filename.gpslc")
```

この関数は、[`GPSLCObject`](@ref) `g` をファイル `<filename>.gpslc` に保存します。この[`GPSLCObject`](@ref)は、含まれている後方サンプルとともに、[`loadGPSLCObject`](@ref) 関数を使用して取得できます。

注意: 拡張子 `.gpslc` はオプションであり、含まれていない場合は追加されます。
