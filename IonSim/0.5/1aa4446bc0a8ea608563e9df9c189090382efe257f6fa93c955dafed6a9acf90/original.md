```
ionprojector(obj, sublevels...; only_ions=false)
```

If `obj<:IonTrap` this will return $|ψ₁⟩⟨ψ₁|⊗...⊗|ψ\_N⟩⟨ψ\_N|⊗𝟙$ where $|ψᵢ⟩$ = `obj.ions[i][sublevels[i]]` and the identity operator $𝟙$ is over all of the COM modes considered in `obj`.

If `only_ions=true`, then the projector is defined only over the ion subspace.

If instead `obj<:Chamber`, then this is the same as `obj = Chamber.iontrap`.
