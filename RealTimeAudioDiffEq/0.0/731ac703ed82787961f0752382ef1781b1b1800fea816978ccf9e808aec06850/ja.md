```
start_DESource(source::DESource, output_device::PaDeviceIndex;
	sample_rate::Float64 = -1., 
	buffer_size::UInt32 = convert(UInt32, paFramesPerBufferUnspecified ))
```

指定された出力デバイスでDESourceを開始します。

# キーワード引数

  * `sample_rate::Float64 = -1.`: ストリームのサンプルレート。負の値の場合、出力デバイスのデフォルトサンプルレートが使用されます。
  * `buffer_size::UInt32 = convert(UInt32, paFramesPerBufferUnspecified )`: ストリームのバッファサイズ。
