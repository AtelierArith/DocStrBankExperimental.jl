```
cglobal((symbol, library) [, type=Cvoid])
```

Cエクスポートされた共有ライブラリ内のグローバル変数へのポインタを取得します。これは[`ccall`](@ref)で指定された通りに正確に指定されます。返されるのは`Ptr{Type}`で、`Type`引数が供給されない場合はデフォルトで`Ptr{Cvoid}`になります。値はそれぞれ[`unsafe_load`](@ref)または[`unsafe_store!`](@ref)によって読み書きできます。
