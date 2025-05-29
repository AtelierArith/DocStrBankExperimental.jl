```
VkFFTPlan{T}(app::Ptr{Cvoid}, config::Ptr{Cvoid}, direction::Int32, dims::NTuple{N, Int} where N, region, buffer_size::AbstractArray{Int}, type::DataType, is_inplace::Bool)
```

VkFFT操作の計画を保持する構造体です。

# フィールド

  * `app::Ptr{Cvoid}`: VkFFT用のFFTW計画に相当します
  * `config::Ptr{Cvoid}`: VkFFFT構成を保持する構造体
  * `direction::Int32`: 前方の場合は-1、逆の場合は1
  * `dims::NTuple{N, Int} where N`: 入力配列のサイズ
  * `region`: FFTを実行する次元
  * `buffer_size::AbstractArray{Int}`: VkFFTが使用するバッファのサイズ（バイト単位）
  * `is_inplace::Bool`: 計画がインプレースであるかどうか（最適化のため）
