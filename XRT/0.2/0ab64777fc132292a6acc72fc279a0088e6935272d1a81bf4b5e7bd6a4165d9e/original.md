Parse a bitstream and generate adapted, typed XRT.Run function for a given kernel or compute unit. Returns tuple of `XRT.Kernel` and `XRT.UUID` object for the specific kernel.

It is recommended to generate the function in a separate module like this:

```Julia
module DummyBitstream
    using XRT
    kernel, uuid = @prepare_run("my_bitstream.xclbin", "dummyKernel", device=device())
end
```

Afterwards, you find the function for the kernel object in the module.

```Julia
julia> DummyBitstream.Run_kernel_name(args...; autostart=true)
```

You can also directly execute a single specific compute unit of the kernel specified by '__':

```Julia
julia> DummyBitstream.Run_kernel_name__cu_name(args...; autostart=true)
```
