```
r2star_crsi!(
    r2s::AbstractArray{<:AbstractFloat, N-1},
    mag::AbstractArray{<:AbstractFloat, N > 1},
    TEs::AbstractVector{<:Real},
    mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing,
    M::Integer = 3,
    sigma::Union{Nothing, Real} = nothing,
    Rsz::NTuple{N-1, Integer} = size(mag)[1:N-1] .÷ 20,
) -> r2s
```

信号統合による緩和率の計算 (CRSI) [1].

### 引数

  * `r2s::AbstractArray{<:AbstractFloat, N-1}`: R2* マップ (1 / TEs の単位)
  * `mag::AbstractArray{<:AbstractFloat, N > 1}`: マルチエコーの大きさ
  * `TEs::AbstractVector{<:Real}`: エコー時間
  * `mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing`: 興味領域のバイナリマスク
  * `M::Integer = 3`: 補間係数
  * `sigma::Union{Nothing, Real} = nothing`: ノイズ
  * `Rsz::NTuple{N-1, Integer} = size(mag)[1:N-1] .÷ 20`:

      * `sigma isa Real`: 未使用
      * `sigma isa Nothing`: 大きさのカーネルは、大きさの背景信号からノイズを計算するために使用されます。

### 戻り値

  * `r2s`: R2* マップ (1 / TEs の単位)

### 参考文献

[1] Song R, Loeffler RB, Holtrop JL, McCarville MB, Hankins JS, Hillenbrand CM.     フィッティングなしでの高速定量パラメータマップ: 統合により正確な単一指数信号減衰率が得られます。     磁気共鳴医学. 2018年6月;79(6):2978-85.
