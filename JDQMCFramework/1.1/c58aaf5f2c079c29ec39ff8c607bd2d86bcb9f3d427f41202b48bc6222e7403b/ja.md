```
local_update_greens!(
    G::AbstractMatrix{T}, logdetG::E, sgndetG::T,
    B::AbstractPropagator{T},
    R::T, Δ::F, i::Int,
    u::AbstractVector{T}, v::AbstractVector{T}
)::Tuple{E,T} where {T<:Number, F<:Number, E<:AbstractFloat}
```

等時グリーン関数行列 `G` をローカル更新によりインプレースで更新します。

# 引数

  * `G::AbstractMatrix{T}`: インプレースで更新される等時グリーン関数行列 $G(\tau,\tau)$。
  * `logdetG::E`: 初期グリーン関数行列の絶対値の対数、$\log( \vert \det G(\tau,\tau) \vert ).$
  * `sgndetG::T`: 初期グリーン関数行列の行列式の符号/位相、$\textrm{sign}( \det G(\tau,\tau) ).$
  * `B::AbstractPropagator{T,E}`: 受け入れられたローカル更新を反映するために更新が必要な伝播子。
  * `R::T`: 行列式比 $R_{l,i} = \frac{\det G(\tau,\tau)}{\det G^\prime(\tau,\tau)}.$
  * `Δ::F`: 指定されたオンサイトエネルギー行列の指数化された変化、$\Delta_{l,i} = e^{-\Delta\tau (V^\prime_{l,(i,i)} - V_{l,(i,i)})} - 1.$
  * `i::Int`: 更新される対角オンサイトエネルギー行列 $V_l$ の行列要素。
  * `u::AbstractVector{T}`: 動的メモリ割り当てを避けるために使用される長さ `size(G,1)` のベクトル。
  * `v::AbstractVector{T}`: 動的メモリ割り当てを避けるために使用される長さ `size(G,2)` のベクトル。

# アルゴリズム

等時グリーン関数行列は次の関係を使用して更新されます。

$$
G_{j,k}^{\prime}\left(\tau,\tau\right)=G_{j,k}\left(\tau,\tau\right)-\frac{1}{R_{l,i}}G_{j,i}\left(\tau,\tau\right)\Delta_{l,i}\left(\delta_{i,k}-G_{i,k}\left(\tau,\tau\right)\right).
$$

伝播子 `B` も更新されます。さらに、このメソッドは $\log( \vert \det G^\prime(\tau,\tau) \vert )$ と $\textrm{sign}( \det G^\prime(\tau,\tau) ).$ を返します。

重要な注意点は、伝播子行列が対称形式で表されている場合、`G′` と `G` は変換された等時グリーン関数行列 $\tilde{G}^\prime(\tau,\tau)$ と $\tilde{G}(\tau,\tau)$ に対応する必要があるということです。詳細については [`local_update_det_ratio`](@ref) ドキュメントを参照してください。
