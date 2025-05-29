ビットストリームを解析し、指定されたカーネルまたは計算ユニットのために適応された型付きの `XRT.Run` 関数を生成します。特定のカーネルのための `XRT.Kernel` と `XRT.UUID` オブジェクトのタプルを返します。

関数を次のように別のモジュールで生成することをお勧めします：

```Julia
module DummyBitstream
    using XRT
    kernel, uuid = @prepare_run("my_bitstream.xclbin", "dummyKernel", device=device())
end
```

その後、モジュール内でカーネルオブジェクトのための関数を見つけることができます。

```Julia
julia> DummyBitstream.Run_kernel_name(args...; autostart=true)
```

また、'__' で指定されたカーネルの特定の計算ユニットを直接実行することもできます：

```Julia
julia> DummyBitstream.Run_kernel_name__cu_name(args...; autostart=true)
```
