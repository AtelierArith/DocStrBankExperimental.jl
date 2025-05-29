Vulkanで使用される特定のドライバーを設定するための便利な関数です。現在、SwiftShaderのみがサポートされています。別のドライバーを追加するには、手動で指定する必要があります。これは、環境変数`VK_DRIVER_FILES`（以前は`VK_ICD_FILENAMES`）を設定して、自分のドライバーJSONマニフェストファイルを指すようにすることで実現できます。詳細はhttps://github.com/KhronosGroup/Vulkan-Loader/blob/main/docs/LoaderDriverInterface.md#driver-discoveryを参照してください。

利用可能なドライバー：

  * SwiftShader: VulkanのCPU実装。`mod`で`SwiftShader_jll`をインポートする必要があります。

```julia
set_driver(backend::Symbol)

```
