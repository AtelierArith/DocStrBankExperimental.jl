構造体タイプの分類。

タイプ:

  * `STYPE_CREATE_INFO`: コンストラクタパラメータを保持します（`CreateInfo`で終わる構造体）。
  * `STYPE_ALLOCATE_INFO`: アロケータパラメータを保持します（`AllocateInfo`で終わる構造体）。
  * `STYPE_GENERIC_INFO`: 他の関数または構造体のパラメータを保持します（前のタイプに該当しない`Info`で終わる構造体）。
  * `STYPE_DATA`: 通常、ユーザーまたはVulkanデータを表します。
  * `STYPE_PROPERTY`: Vulkanによって`returnedonly`構造体で返されるプロパティで、通常は`FTYPE_QUERY`タイプの関数を通じて行われます。

```julia
primitive type StructType <: Enum{Int32} 32
```
