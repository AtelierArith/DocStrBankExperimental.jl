```julia
mutable struct LazyBufferedTIFF{T<:Union{ColorTypes.Colorant, TiffImages.WidePixel}, O<:Unsigned, AA<:AbstractArray} <: TiffImages.AbstractDenseTIFF{T<:Union{ColorTypes.Colorant, TiffImages.WidePixel}, 3}
```

遅延読み込みTIFFデータを表す型で、`TiffImages.load(filepath; lazyio=true)`によって返されます。メモリに保存するには大きすぎる画像を開いて操作するのに便利で、新しいTIFFファイルを段階的に書き込むためにも使用されます。

これは個々のスライスをバッファリングすることによって機能します。これにより、圧縮TIFFを含む幅広いフォーマットのサポートが可能ですが、特定のアクセス（インデックス）パターンに応じてパフォーマンスが異なります。パッケージのドキュメントでの議論や、異なる強みと弱みを持つ代替手段として[`MmappedTIFF`](@ref)を参照してください。

```jldoctest
julia> using TiffImages, ColorTypes

julia> img = empty(LazyBufferedTIFF, Gray{Float32}, joinpath(mktempdir(), "test.tif"))
32-bit LazyBufferedTIFF{Gray{Float32}} 0×0×0 (writable)
    Current file size on disk:   8 bytes
    Addressable space remaining: 4.000 GiB

julia> close(img) # 作業が完了したら、ストリームを閉じます
```

  * `file`: バッキングファイルを追跡するためのポインタ
  * `ifds`: この配列内の各スライスに関連付けられたタグ
  * `dims`
  * `working_cache`: ディスクから読み込むために埋める内部キャッシュ
  * `cache`: 完全に変換されたデータで埋める内部キャッシュ
  * `cache_index`: 現在読み込まれているスライスのインデックス
  * `last_ifd_offset`: 最後に読み込まれたIFDの位置で、スライスが追加されるたびに更新されます
  * `readonly`: このファイルが編集可能かどうかを追跡するフラグ
