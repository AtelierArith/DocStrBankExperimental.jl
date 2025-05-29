```
movingwindow(vec::AbstractVector; kwargs...)::AbstractVector{UnitRange{Int}}
movingwindow(npoints::Integer; kwargs...)::AbstractVector{UnitRange{Int}}
```

一定数の等間隔のウィンドウ（すなわち、整数インデックスのベクター）を返し、ベクター `vec`（または `npoints` 値のベクター）をスライスするために使用されます。

```
movingwindow(f::Base.Callable, vec::AbstractVector; kwargs...)::AbstractVector
```

`vec` のウィンドウスライシングに対する `f` の `map` を返します。

キーワード引数に関しては、異なる使用ケースに応じてこの関数の異なるフレーバーが利用可能です。

# 固定サイズのウィンドウ

```
function movingwindow(
    npoints::Integer;
    window_size::Union{Nothing,Real} = nothing,
    window_step::Union{Nothing,Real} = nothing,
    # オプションの引数
    landmark::Union{Integer,Nothing} = nothing,
    allow_landmark_position::Tuple{<:AbstractFloat,<:AbstractFloat} = (0.0, 1.0),
    kwargs...
)::AbstractVector{UnitRange{Int}}
```

長さ `window_size` のウィンドウを返し、連続するウィンドウ間のステップは `window_step` です。`window_step` が浮動小数点数の場合、返されるウィンドウ内のステップは一定ではなく、`window_step` の周りで変動します。

関数に `landmark::Integer` ポイントが指定されると、ランドマークを含むウィンドウのみが返されます。例えば、`npoints=100` で `landmark=50` の場合、すべてのウィンドウは `50` を含みます。また、`allow_landmark_position` を使用してウィンドウ内のランドマークの相対位置の範囲を指定することも可能です。

# 固定数のウィンドウ

```
function movingwindow(
    npoints::Integer;
    nwindows::Union{Nothing,Integer} = nothing,
    relative_overlap::Union{Nothing,AbstractFloat} = nothing,
    kwargs...
)::AbstractVector{UnitRange{Int}}
```

`nwindows` ウィンドウを計算し、連続するウィンドウは `relative_overlap` に等しい部分で重なります。

# 固定サイズのウィンドウの固定数

```
function movingwindow(
    npoints::Integer;
    nwindows::Union{Nothing,Integer} = nothing,
    window_size::Union{Nothing,Real} = nothing,
    kwargs...
)::AbstractVector{UnitRange{Int}}
```

長さ `window_size` の `nwindows` ウィンドウを計算します。

# 例

TODO

長さ `window_size` のウィンドウを計算し、連続するウィンドウは `window_step` 単位だけシフトされます。
