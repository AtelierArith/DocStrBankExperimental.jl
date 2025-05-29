```
effective_hamiltonian(bw::WaveguideBasis{Np,Nw},bs,C,G) where {Np,Nw}
```

基底 `bw` がローカルエミッタ/キャビティ `bc` に結合された波導システムの有効ハミルトニアンを返します。ここでの `C` と `G` は、結合の入力出力関係を決定し、次のようになります: $\frac{d}{d t} a=-i\left[a, H_{\mathrm{c}}\right]-\Sigma a+\mathbf{k}^T \mathbf{W}_{\mathrm{in}}$、および $\mathbf{W}_{\text {out }}(t)=\mathbf{C} \mathbf{W}_{\mathrm{in}}(t)+a(t)\mathbf{d}$。ここで $\tilde{\mathbf{d}} =  \tilde{\mathbf{k}} = -i \left(\left(\mathbf{I}+\frac{i}{2} \mathbf{V}\right)^{-1} \right) \mathbf{\Gamma}$、ここで $\mathbf{\Gamma}$ は `G` ベクトルによって決定され、`bw` の波導の数と同じ長さになります。ここでの $\mathbf{C}$ は、次元 (nw,nw) の `C` であり、nw は `bw` の波導の数です。

このハミルトニアンを用いてシミュレーションした結果の状態 $\ket{\tilde{\psi}}_{\mathrm{out}}$ は、正しい入力出力関係を得るために [`WaveguideTransform`](@ref) を使用して変換する必要があります。すなわち、$\ket{\psi}_{\mathrm{out}} = \mathbf{C} \ket{\tilde{\psi}}_{\mathrm{out}}$ となります。

例:

```
times = 0:0.1:10
dt = times[2] - times[1]

bw = WaveguideBasis(1,2,times)
be = FockBasis(1)


C = [0 -1.0im; -1.0im 0]
γ=1
G = [sqrt(γ/dt),sqrt(γ/dt)]

H = effective_hamiltonian(bw,be,C,G)

ξfun(t1,σ,t0) = sqrt(2/σ)* (log(2)/pi)^(1/4)*exp(-2*log(2)*(t1-t0)^2/σ^2)

ψ_in = onephoton(bw,1,ξfun,1,5) ⊗ fockstate(be,0)
ψ_out_tilde = waveguide_evolution(times,ψ_in,H)


C_transform = WaveguideTransform(bw,C) ⊗ identityoperator(be)
ψ_out = C_transform*ψ_out_tilde
```
