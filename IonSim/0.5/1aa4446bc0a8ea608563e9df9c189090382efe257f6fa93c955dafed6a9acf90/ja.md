```
ionprojector(obj, sublevels...; only_ions=false)
```

もし `obj<:IonTrap` の場合、これは $|ψ₁⟩⟨ψ₁|⊗...⊗|ψ\_N⟩⟨ψ\_N|⊗𝟙$ を返します。ここで $|ψᵢ⟩$ = `obj.ions[i][sublevels[i]]` であり、単位演算子 $𝟙$ は `obj` で考慮されるすべてのCOMモードにわたります。

もし `only_ions=true` の場合、プロジェクターはイオンサブスペースのみに対して定義されます。

代わりに `obj<:Chamber` の場合、これは `obj = Chamber.iontrap` と同じです。
