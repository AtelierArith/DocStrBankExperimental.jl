```julia
Xclbin(path::AbstractString) -> XRT.Xclbin

```

Structure that allows a more convenient access to parameters provided `XRTWrap.Xclbin` type. Nevertheless, this type can be called with the field `xclbin` if required. With the instantiation of an `Xclbin` object several checks, such as the path or the target type are performed.

**Fields**

**`xclbin`** allows access to the `XRT.XRTWrap.Xclbin` object if required.

**`path`** is the absolute path that leads to the xclbin file.

**`filename`** is the file name of the xclbin file including the file extension.

**`kernels`** specifies a vector of [`XRT.XclbinKernel`](@ref) type objects. These elements provide information of all kernels given in the metadata.

**`ips`** specifies a vector of [`XRT.XclbinIP`](@ref) type objects. These elements represent the IP_LAYOUT section of the xclbin file.

**`mems`** specifies a vector of [`XRT.XclbinMem`](@ref) type objects.

**`xsa_name`** is the Xilinx Support Archive name of the xclbin file.

**`uuid`** is the UUID of the xclbin file.

**`fpga_device_name`** is the name of the FPGA device according to the metadata.

**`target_type`** is the type of the xlbin file. It is either set to `hw`, `hw_emu`, or `sw_emu`.

**`interface_uuid`** is the interface UUID when device is programmed with 2RP shell. Only available for XRT ≥ 2.16.
