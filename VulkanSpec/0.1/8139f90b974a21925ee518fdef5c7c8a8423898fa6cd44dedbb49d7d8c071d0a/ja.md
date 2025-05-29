関数タイプの分類。

タイプ:

  * `FTYPE_CREATE`: コンストラクタ（`vkCreate`で始まる関数）。
  * `FTYPE_DESTROY`: デストラクタ（`vkDestroy`で始まる関数）。
  * `FTYPE_ALLOCATE`: アロケータ（`vkAllocate`で始まる関数）。
  * `FTYPE_FREE`: デアロケータ（`vkFree`で始まる関数）。
  * `FTYPE_COMMAND`: Vulkanコマンド（`vkCmd`で始まる関数）。
  * `FTYPE_QUERY`: パラメータをクエリするために使用され、ポインタの変異を通じて直接または間接的に返される（通常、`vkEnumerate`および`vkGet`で始まる関数だが、すべてではなく、他の可能性もある）。
  * `FTYPE_OTHER`: 特定のタイプなし。

```julia
primitive type FunctionType <: Enum{Int32} 32
```
