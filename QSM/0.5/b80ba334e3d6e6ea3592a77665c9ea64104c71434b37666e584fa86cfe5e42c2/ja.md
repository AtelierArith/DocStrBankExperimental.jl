```
r2star_crsi(
    mag::AbstractArray{<:AbstractFloat, N > 1},
    TEs::AbstractVector{<:Real},
    mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing;
    M::Integer = 3,
    sigma::Union{Nothing, Real} = nothing,
    Rsz::NTuple{N-1, Integer} = size(mag)[1:N-1] .÷ 20,
) -> typeof(similar(mag, size(mag)[1:N-1]))
```

信号統合による緩和率の計算 (CRSI) [1].

### 引数

  * `mag::AbstractArray{<:AbstractFloat, N > 1}`: マルチエコーの大きさ
  * `TEs::AbstractVector{<:Real}`: エコー時間
  * `mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing`: 興味のある領域のバイナリマスク

### キーワード

  * `M::Integer = 3`: 補間係数
  * `sigma::Union{Nothing, Real} = nothing`: ノイズ
  * `Rsz::NTuple{N-1, Integer} = size(mag)[1:N-1] .÷ 20`:

      * `sigma isa Real`: 未使用
      * `sigma isa Nothing`: 大きさのカーネルは、マグニチュードの背景信号からノイズを計算するために使用されます。

### 戻り値

  * `typeof(similar(mag, size(mag)[1:N-1]))`: R2* マップ (1 / TEsの単位)

### 参考文献

[1] Song R, Loeffler RB, Holtrop JL, McCarville MB, Hankins JS, Hillenbrand CM.     フィッティングなしでの高速定量パラメータマップ: 統合により正確な単一指数信号減衰率が得られます。     医学における磁気共鳴. 2018年6月;79(6):2978-85.
