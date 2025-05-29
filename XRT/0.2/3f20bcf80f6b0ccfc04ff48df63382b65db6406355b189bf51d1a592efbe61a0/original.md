Parse a bitstream and generate functions for the included kernels. The functions will automatically copy all relevant buffers to the FPGA memory, and execute the Kernel.

It is recommended to generate the kernel functions in a separate module like this:

```Julia
module DummyBitstream
    using XRT
    @prepare_bitstream("my_bitstream.xclbin")
end
```

Afterwards, you find the functions for each kernel in the module. To execute the kernel on a device other than the current active device, use the `device` keyword parameter:

```Julia
julia> DummyBitstream.kernel_name!(args...; device=XRT.device(2))
```

You can also directly execute a single specific compute unit of the kernel specified by '__':

```Julia
julia> DummyBitstream.kernel_name__cu_name!(args...)
```
