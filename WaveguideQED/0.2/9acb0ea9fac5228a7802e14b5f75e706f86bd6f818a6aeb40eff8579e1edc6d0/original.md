```
effective_hamiltonian(bw::WaveguideBasis{Np,Nw},bs,C,G) where {Np,Nw}
```

Return the effective Hamiltonian for a waveguide system with basis `bw` coupled to a local emitter/cavity with the basis `bc`. `C` and `G` here determine the input output relations of the coupling such that: $\frac{d}{d t} a=-i\left[a, H_{\mathrm{c}}\right]-\Sigma a+\mathbf{k}^T \mathbf{W}_{\mathrm{in}}$, and $\mathbf{W}_{\text {out }}(t)=\mathbf{C} \mathbf{W}_{\mathrm{in}}(t)+a(t)\mathbf{d}$.  Here $\tilde{\mathbf{d}} =  \tilde{\mathbf{k}} = -i \left(\left(\mathbf{I}+\frac{i}{2} \mathbf{V}\right)^{-1} \right) \mathbf{\Gamma}$, where $\mathbf{\Gamma}$ is determined by the vector `G` with a length equal to the number of waveguide in `bw`. $\mathbf{C}$ is here given by `C` which is of dimensions (nw,nw) with nw being the number of waveguides in `bw`.

The resulting state $\ket{\tilde{\psi}}_{\mathrm{out}}$ from simulating with this Hamiltonian needs to be transformed using [`WaveguideTransform`](@ref) such that $\ket{\psi}_{\mathrm{out}} = \mathbf{C} \ket{\tilde{\psi}}_{\mathrm{out}}$ to get the correct input-output relations.

Examples:

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
