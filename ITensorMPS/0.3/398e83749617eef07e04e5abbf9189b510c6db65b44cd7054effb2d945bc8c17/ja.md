```
@preserve_ortho
```

MPS/MPOの直交性制限を保持するブロックコードを指定します。最初の入力は、直交性制限を保持する必要がある単一のMPS/MPOまたはMPS/MPOのタプルです。

# 例

```julia
s = siteinds("S=1/2", 4)

# ボンド次元2のランダムMPSを作成
ψ₁ = random_mps(s, "↑"; linkdims=2)
ψ₂ = random_mps(s, "↑"; linkdims=2)
ψ₁ = orthogonalize(ψ₁, 1)
ψ₂ = orthogonalize(ψ₂, 1)

# ortho_lims(ψ₁) = 1:1
@show ortho_lims(ψ₁)

# ortho_lims(ψ₂) = 1:1
@show ortho_lims(ψ₂)

@preserve_ortho (ψ₁, ψ₂) begin
  ψ₁ .= addtags.(ψ₁, "x₁"; tags = "Link")
  ψ₂ .= addtags.(ψ₂, "x₂"; tags = "Link")
end

# ortho_lims(ψ₁) = 1:1
@show ortho_lims(ψ₁)

# ortho_lims(ψ₂) = 1:1
@show ortho_lims(ψ₂)
```
