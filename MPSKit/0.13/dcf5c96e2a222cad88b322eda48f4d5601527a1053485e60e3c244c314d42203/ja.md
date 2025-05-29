```
WindowMPS{A<:GenericMPSTensor,B<:MPSBondTensor} <: AbstractFiniteMPS
```

有限行列積状態を無限行列積状態に埋め込んだ型。

## フィールド

  * `left_gs::InfiniteMPS` – 左の無限環境
  * `window::FiniteMPS` – 有限ウィンドウ行列積状態
  * `right_gs::InfiniteMPS` – 右の無限環境

---

## コンストラクタ

```
WindowMPS(left_gs::InfiniteMPS, window_state::FiniteMPS, [right_gs::InfiniteMPS])
WindowMPS(left_gs::InfiniteMPS, window_tensors::AbstractVector, [right_gs::InfiniteMPS])
WindowMPS([f, eltype], physicalspaces::Vector{<:Union{S, CompositeSpace{S}},
          virtualspaces::Vector{<:Union{S, CompositeSpace{S}}, left_gs::InfiniteMPS,
          [right_gs::InfiniteMPS])
WindowMPS([f, eltype], physicalspaces::Vector{<:Union{S,CompositeSpace{S}}},
          maxvirtualspace::S, left_gs::InfiniteMPS, [right_gs::InfiniteMPS])
```

左と右の無限環境を指定し、ウィンドウ状態またはウィンドウを構築するためのテンソルのベクトルのいずれかを使用してWindowMPSを構築します。あるいは、[`FiniteMPS`](@ref)のコンストラクタと同じ引数を提供し、その後に左（および右）環境を指定してWindowMPSを一度に構築することも可能です。

!!! note
    デフォルトでは、右の環境は左と等しく選択されますが、コピーは作成されません。この場合、左の状態を変更すると右の状態にも影響します。

    WindowMPS(state::InfiniteMPS, L::Int)


InfiniteMPSからWindowMPSを構築し、長さ`L`の領域を`FiniteMPS`に昇格させます。
