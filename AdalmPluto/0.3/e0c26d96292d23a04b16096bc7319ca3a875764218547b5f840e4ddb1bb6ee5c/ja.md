```
PlutoSDR
+-- ctx::Ptr{iio_context}
|
+-- tx::PlutoTx
|   |
|   +-- iio::txWrapper
|   |   |
|   |   +-- tx::Ptr{iio_device};
|   |   +-- tx0_i::Ptr{iio_channel};
|   |   +-- tx0_q::Ptr{iio_channel};
|   |   +-- chn::Ptr{iio_channel};
|   |   +-- chn_lo::Ptr{iio_channel};
|   |
|   +-- cfg::ChannelCfg
|   |   |
|   |   +-- rfport::String;
|   |   +-- bandwidth::Int64;
|   |   +-- samplingRate::Int64;
|   |   +-- carrierFreq::Int64;
|   |
|   +-- buf::IIO_Buffer
|   |   |
|   |   +-- C_ptr::Ptr{iio_buffer};         |< Cバッファへのポインタ
|   |   +-- C_size::Csize_t;                |< サンプル数におけるCバッファのサイズ
|   |   +-- C_sample_size::Cssize_t;        |< Cバッファ内のサンプルのサイズ
|   |   +-- C_first::Ptr{Cuchar};           |< Cバッファ内の最初のサンプルへのポインタ
|   |   +-- C_last::Ptr{Cuchar};            |< Cバッファ内の最後のサンプルへのポインタ
|   |   +-- C_step::Cssize_t;               |< Cバッファ内のサンプルポインタ間の距離
|   |   +-- i_raw_samples::Array{UInt8}     |< Iバイトを格納するための一時バッファ
|   |   +-- q_raw_samples::Array{UInt8}     |< Qバイトを格納するための一時バッファ
|   |   +-- samples::Array{ComplexF32}      |< Julia配列に格納されたサンプル
|   |   +-- nb_samples::Int                 |< Julia配列内のサンプル数
|   |
|   +-- effectiveSamplingRate::Float64
|   +-- effectiveCarrierFreq::Float64
|   +-- released::Bool
|
+-- rx::PlutoRx
|   |
|   +-- iio::rxWrapper
|   |   +-- rx::Ptr{iio_device};
|   |   +-- rx0_i::Ptr{iio_channel};
|   |   +-- rx0_q::Ptr{iio_channel};
|   |   +-- chn::Ptr{iio_channel};
|   |   +-- chn_lo::Ptr{iio_channel};
|   |
|   +-- cfg::ChannelCfg
|   |   |
|   |   +-- rfport::String;
|   |   +-- bandwidth::Int64;
|   |   +-- samplingRate::Int64;
|   |   +-- carrierFreq::Int64;
|   |
|   +-- buf::IIO_Buffer
|   |   |
|   |   +-- C_ptr::Ptr{iio_buffer};         |< Cバッファへのポインタ
|   |   +-- C_size::Csize_t;                |< サンプル数におけるCバッファのサイズ
|   |   +-- C_sample_size::Cssize_t;        |< Cバッファ内のサンプルのサイズ
|   |   +-- C_first::Ptr{Cuchar};           |< Cバッファ内の最初のサンプルへのポインタ
|   |   +-- C_last::Ptr{Cuchar};            |< Cバッファ内の最後のサンプルへのポインタ
|   |   +-- C_step::Cssize_t;               |< Cバッファ内のサンプルポインタ間の距離
|   |   +-- i_raw_samples::Array{UInt8}     |< Iバイトを格納するための一時バッファ
|   |   +-- q_raw_samples::Array{UInt8}     |< Qバイトを格納するための一時バッファ
|   |   +-- samples::Array{ComplexF32}      |< デコードされてJulia配列に格納されたサンプル
|   |   +-- nb_samples::Int                 |< Julia配列内で利用可能なサンプル数
|   |
|   +-- effectiveSamplingRate::Float64
|   +-- effectiveCarrierFreq::Float64
|   +-- released::Bool
|
+-- released::Bool
```
