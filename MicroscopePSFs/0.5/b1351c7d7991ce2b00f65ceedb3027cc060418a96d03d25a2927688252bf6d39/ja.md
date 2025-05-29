```
integrate_pixels_amplitude(
    psf::AbstractPSF, 
    pixel_edges_x::AbstractVector,
    pixel_edges_y::AbstractVector,
    emitter::AbstractEmitter; 
    support::Union{Real,Tuple{<:Real,<:Real,<:Real,<:Real}} = Inf,
    sampling::Integer=2,
    threaded::Bool=true
)
```

カメラのピクセル上でPSFの複素振幅を統合し、オプションのサポート領域最適化を行います。

指定された領域内の各ピクセルについて、指定されたサンプリング密度を使用してPSF振幅を数値的に統合します。強度統合とは異なり、コヒーレント計算に使用できる非正規化の複素振幅を返します。PSFとエミッタの両方がサポートしている場合、z座標を自動的に処理します。

# 引数

  * `psf::AbstractPSF`: 統合する点拡散関数
  * `pixel_edges_x::AbstractVector`: マイクロメートル単位のピクセルのX座標エッジ
  * `pixel_edges_y::AbstractVector`: マイクロメートル単位のピクセルのY座標エッジ
  * `emitter::AbstractEmitter`: カメラに対してマイクロメートル単位で位置を持つエミッタ
  * `support`: 計算する領域（デフォルト: Inf = 全画像）

      * Realの場合: エミッタの周りの半径（マイクロメートル単位）
      * Tupleの場合: 明示的な（x*min, x*max, y*min, y*max）（マイクロメートル単位）
  * `sampling::Integer=2`: 各次元のピクセルあたりのサンプル数
  * `threaded::Bool=true`: 統合にマルチスレッドを使用するかどうか

# 戻り値

  * `Matrix{Complex{T}}`: エミッタのphotons型に一致する統合された複素振幅
  * 配列は[y,x]でインデックス付けされ、[1,1]が左上のピクセル
  * 値は複素振幅の関係を保持するために正規化されていません

# 注意事項

  * コヒーレント計算には、この関数を`integrate_pixels`の代わりに使用してください
  * 戻り値の型は、位相情報を持つPSFをサポートするために複素です
  * 振幅から強度を得るには: `abs2.(integrate_pixels_amplitude(...))`

参照: [`integrate_pixels`](@ref), [`AbstractPSF`](@ref)
