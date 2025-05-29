```
levelsetlattice(sgnum::Integer, D::Integer=2, idxmax::NTuple=ntuple(i->2,D))
    --> UnityFourierLattice{D}
```

空の「中立的」なフーリエ格子基底、すなわち [`UnityFourierLattice`](@ref) を、次元 `D` における空間群 `sgnum` の対称性に一致するように計算します。結果として得られる格子 `flat` は、対称性に由来する軌道に分割されたフーリエ基底で展開され、軌道内の係数は空間群の対称性によって制約されます。しかし、軌道間の係数は自由で制約されていません。

各逆格子ベクトルに沿ったフーリエ解像度は `idxmax` によって制御されます。例えば、`D = 2` で `idxmax = (2, 3)` の場合、結果として得られるフーリエ格子は、k₁∈[0,±1,±2] および k₂∈[0,±1,±2,±3] を持つ逆格子ベクトル (k₁, k₂) を含む可能性があり、これは 𝐆-基底に関連付けられます。

この「中立的」な格子は、通常 [`modulate`](@ref) によってその後変調されるべきです（これは軌道間の係数を変調し、「中立的」な構成に存在する可能性のある「合成対称性」を排除することができます。これは、すべての軌道間の係数が1に設定されているためです）。

## 例

`UnityFourierLattice` を計算し、`modulate` を介してランダムな軌道間の係数で変調し、最後にそれをプロットします（PyPlot.jlを介して）：

```julia-repl
julia> uflat = levelsetlattice(16, Val(2))
julia> flat  = modulate(uflat)
julia> Rs    = directbasis(16, Val(2)) 
julia> using PyPlot
julia> plot(flat, Rs)
```
