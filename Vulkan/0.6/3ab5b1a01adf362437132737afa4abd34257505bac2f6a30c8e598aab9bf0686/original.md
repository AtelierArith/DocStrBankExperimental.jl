# Vulkan

![tests](https://github.com/JuliaGPU/Vulkan.jl/workflows/CI/badge.svg) [![](https://img.shields.io/badge/docs-stable-blue.svg)](https://juliagpu.github.io/Vulkan.jl/stable) [![](https://img.shields.io/badge/docs-dev-blue.svg)](https://juliagpu.github.io/Vulkan.jl/dev)

Vulkan.jl is a lightweight wrapper around the [Vulkan](https://www.vulkan.org/) graphics and compute library. It exposes abstractions over the underlying C interface, primarily geared towards developers looking for a more natural way to work with Vulkan with minimal overhead.

It builds upon the core API provided by [VulkanCore.jl](https://github.com/JuliaGPU/VulkanCore.jl/). Because Vulkan is originally a C specification, interfacing with it requires some knowledge before correctly being used from Julia. This package acts as an abstraction layer, so that you don't need to know how to properly call a C library, while still retaining full functionality. The wrapper is generated directly from the [Vulkan Specification](https://www.khronos.org/registry/vulkan/).

This is a very similar approach to that taken by [VulkanHpp](https://github.com/KhronosGroup/Vulkan-Hpp), except that the target language is Julia and not C++.

If you have questions, want to brainstorm ideas or simply want to share cool things you do with Vulkan don't hesitate to create a thread in our [Zulip channel](https://julialang.zulipchat.com/#narrow/stream/287693-vulkan).

## Status

This package is a work in progress and has not reached its 1.0 version yet. As such, documentation may not be complete and functionality may change without warning. If it happens, make sure to check out the [changelog](https://github.com/JuliaGPU/Vulkan.jl/blob/main/CHANGELOG.md). At this stage, you should not use this library in production; however, you are encouraged to push its boundaries through non-critical projects. If you find limitations, bugs or want to suggest potential improvements, do not hesitate to submit issues or pull requests. The goal is definitely to be production-ready as soon as possible.

In particular, because the library relies on automatic code generation, there may be portions of the Vulkan API that are not wrapped correctly. While you should not have trouble in most cases, there are always edge cases which were not accounted for during generation. Please open an issue whenever you encounter such a case, so that we can reliably fix those wrapping issues for future use.

## Testing

Currently, continuous integration runs only on Ubuntu 32/64 bits, for lack of a functional CI setup with Vulkan for MacOS and Windows. Because public CI services lack proper driver support, the CPU Vulkan implementation [Lavapipe](https://docs.mesa3d.org/drivers/llvmpipe.html) is used. If you are not on Linux, we cannot guarantee that this library will work for you, although so far nothing is platform-dependent. If that is the case, we recommend that you test this package with your own setup.

Depends on:

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
