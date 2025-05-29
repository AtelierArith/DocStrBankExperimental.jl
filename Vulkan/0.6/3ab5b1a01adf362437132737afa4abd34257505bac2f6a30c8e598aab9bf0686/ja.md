# Vulkan

![tests](https://github.com/JuliaGPU/Vulkan.jl/workflows/CI/badge.svg) [![](https://img.shields.io/badge/docs-stable-blue.svg)](https://juliagpu.github.io/Vulkan.jl/stable) [![](https://img.shields.io/badge/docs-dev-blue.svg)](https://juliagpu.github.io/Vulkan.jl/dev)

Vulkan.jlは、[Vulkan](https://www.vulkan.org/)グラフィックスおよび計算ライブラリの軽量ラッパーです。これは、主にオーバーヘッドを最小限に抑えた自然な方法でVulkanを操作したい開発者向けに、基盤となるCインターフェースの抽象化を提供します。

これは、[VulkanCore.jl](https://github.com/JuliaGPU/VulkanCore.jl/)によって提供されるコアAPIに基づいています。Vulkanは元々Cの仕様であるため、Juliaから正しく使用するにはいくつかの知識が必要です。このパッケージは抽象化レイヤーとして機能し、Cライブラリを正しく呼び出す方法を知らなくても、完全な機能を保持します。ラッパーは、[Vulkan Specification](https://www.khronos.org/registry/vulkan/)から直接生成されています。

これは、[VulkanHpp](https://github.com/KhronosGroup/Vulkan-Hpp)が取っているアプローチと非常に似ていますが、ターゲット言語はC++ではなくJuliaです。

質問がある場合、アイデアをブレインストーミングしたい場合、またはVulkanで行っているクールなことを共有したい場合は、遠慮なく私たちの[Zulip channel](https://julialang.zulipchat.com/#narrow/stream/287693-vulkan)でスレッドを作成してください。

## ステータス

このパッケージは進行中の作業であり、まだ1.0バージョンには達していません。そのため、ドキュメントが完全でない場合や、機能が予告なしに変更される場合があります。そうなった場合は、[changelog](https://github.com/JuliaGPU/Vulkan.jl/blob/main/CHANGELOG.md)を確認してください。この段階では、このライブラリを本番環境で使用しないことをお勧めしますが、非クリティカルなプロジェクトを通じてその限界を押し広げることを奨励します。制限やバグを見つけた場合、または潜在的な改善を提案したい場合は、問題やプルリクエストを提出することをためらわないでください。目標は、できるだけ早く本番環境に対応できるようにすることです。

特に、このライブラリは自動コード生成に依存しているため、正しくラップされていないVulkan APIの部分があるかもしれません。ほとんどの場合、問題はないはずですが、生成中に考慮されなかったエッジケースが常に存在します。そのようなケースに遭遇した場合は、必ず問題をオープンしてください。将来の使用のために、これらのラッピングの問題を確実に修正できるようにします。

## テスト

現在、継続的インテグレーションはUbuntu 32/64ビットでのみ実行されており、MacOSおよびWindows用のVulkanの機能的なCIセットアップが不足しています。公共のCIサービスは適切なドライバーサポートが不足しているため、CPU Vulkan実装の[Lavapipe](https://docs.mesa3d.org/drivers/llvmpipe.html)が使用されています。Linux以外の環境では、このライブラリが機能することを保証できませんが、これまでのところプラットフォームに依存するものはありません。その場合は、自分のセットアップでこのパッケージをテストすることをお勧めします。

依存関係:

  * `Base`
  * `BitMasks`
  * `Core`
  * `DocStringExtensions`
  * `Logging`
  * `MLStyle`
  * `PrecompileTools`
  * `Reexport`
  * `Vulkan.CEnum`
  * `VulkanCore.LibVulkan`
