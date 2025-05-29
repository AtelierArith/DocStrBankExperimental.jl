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
|   |   +-- C_ptr::Ptr{iio_buffer};         |< Pointer to the C buffer
|   |   +-- C_size::Csize_t;                |< Size of the C buffer in samples
|   |   +-- C_sample_size::Cssize_t;        |< Size of a sample in the C buffer
|   |   +-- C_first::Ptr{Cuchar};           |< Pointer to the first sample in the C buffer
|   |   +-- C_last::Ptr{Cuchar};            |< Pointer to the last sample in the C buffer
|   |   +-- C_step::Cssize_t;               |< Distance between to sample pointers in the C buffer
|   |   +-- i_raw_samples::Array{UInt8}     |< Temporary buffer to store I bytes
|   |   +-- q_raw_samples::Array{UInt8}     |< Temporary buffer to store Q bytes
|   |   +-- samples::Array{ComplexF32}      |< Samples stored in a Julia array
|   |   +-- nb_samples::Int                 |< Number of samples in the Julia array
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
|   |   +-- C_ptr::Ptr{iio_buffer};         |< Pointer to the C buffer
|   |   +-- C_size::Csize_t;                |< Size of the C buffer in samples
|   |   +-- C_sample_size::Cssize_t;        |< Size of a sample in the C buffer
|   |   +-- C_first::Ptr{Cuchar};           |< Pointer to the first sample in the C buffer
|   |   +-- C_last::Ptr{Cuchar};            |< Pointer to the last sample in the C buffer
|   |   +-- C_step::Cssize_t;               |< Distance between to sample pointers in the C buffer
|   |   +-- i_raw_samples::Array{UInt8}     |< Temporary buffer to store I bytes
|   |   +-- q_raw_samples::Array{UInt8}     |< Temporary buffer to store Q bytes
|   |   +-- samples::Array{ComplexF32}      |< Samples decoded and stored in a Julia array
|   |   +-- nb_samples::Int                 |< Number of samples available in the Julia array
|   |
|   +-- effectiveSamplingRate::Float64
|   +-- effectiveCarrierFreq::Float64
|   +-- released::Bool
|
+-- released::Bool
```
