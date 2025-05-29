```
fourier_transform!(
    C::AbstractArray{Complex{T}},
    a::Int,
    b::Int,
    dims,
    unit_cell::UnitCell{D,T},
    lattice::Lattice{D}
) where {D, T<:AbstractFloat}

fourier_transform!(C::AbstractArray{Complex{T}},
    a::Int,
    b::Int,
    unit_cell::UnitCell{D,T},
    lattice::Lattice{D}
) where {D, T<:AbstractFloat}
```

位置から運動量空間へのフーリエ変換を計算します

$$
\begin{align*}
C_{\mathbf{k}}^{a,b}= & \sum_{\mathbf{r}}e^{{\rm -i}\mathbf{k}\cdot(\mathbf{r}+\mathbf{r}_{a}-\mathbf{r}_{b})}C_{\mathbf{r}}^{a,b}
\end{align*}
$$

ここで、$a$ と $b$ は単位セル内の軌道種を指定します。配列 `C` はインプレースで修正されることに注意してください。`dims` が渡されると、配列のこれらの次元を反復処理し、各スライスに対してフーリエ変換を実行します。
