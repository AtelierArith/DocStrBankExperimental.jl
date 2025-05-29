ビットストリームを解析し、含まれているカーネルのための関数を生成します。これらの関数は、関連するすべてのバッファをFPGAメモリに自動的にコピーし、カーネルを実行します。

カーネル関数は、次のように別のモジュールで生成することをお勧めします：

```Julia
module DummyBitstream
    using XRT
    @prepare_bitstream("my_bitstream.xclbin")
end
```

その後、モジュール内で各カーネルの関数を見つけることができます。現在のアクティブデバイス以外のデバイスでカーネルを実行するには、`device`キーワードパラメータを使用します：

```Julia
julia> DummyBitstream.kernel_name!(args...; device=XRT.device(2))
```

特定のカーネルの特定の計算ユニットを直接実行することもできます：

```Julia
julia> DummyBitstream.kernel_name__cu_name!(args...)
```
