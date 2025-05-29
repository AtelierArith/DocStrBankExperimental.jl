```
CuPrimaryContext(dev::CuDevice)
```

Create a primary CUDA context for a given device.

Each primary context is unique per device and is shared with CUDA runtime API. It is meant for interoperability with (applications using) the runtime API.
