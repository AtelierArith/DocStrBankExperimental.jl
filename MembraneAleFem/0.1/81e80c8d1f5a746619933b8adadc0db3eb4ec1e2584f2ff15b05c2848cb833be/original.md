```
GeoDynStress(xms, cps, dofs, N, ∂Nα, ∂∂Nαβ, p::Params)
```

Container for all geometric, dynamic, and stress-related quantities at a single point $(ζ^1, ζ^2)$.

Accessible fields:

|   code   |                  symbol                  |
|:--------:|:----------------------------------------:|
|   `𝘅`    |                 $\bm{x}$                 |
|  `𝗮_α`   |                $\bm{a}_α$                |
| `∂∂𝘅αβ`  |             $\bm{x}_{, α β}$             |
|  `a_αβ`  |                $a_{α β}$                 |
|  `a△αβ`  |                $a^{α β}$                 |
|  `𝗮△α`   |                $\bm{a}^α$                |
|   `JΩ`   |               $J_{\Omega}$               |
| `Γ△μ_αβ` |       $\Gamma^\mu_{\alpha \beta}$        |
|   `𝗻`    |                 $\bm{n}$                 |
|  `b_αβ`  |                $b_{α β}$                 |
|   `H`    |                   $H$                    |
|   `K`    |                   $K$                    |
|   `𝘃`    |                 $\bm{v}$                 |
|  `∂𝘃α`   |              $\bm{v}_{, α}$              |
| `∂∂𝘃αβ`  |             $\bm{v}_{, α β}$             |
|   `λ`    |                   $λ$                    |
|   `pm`   |              $p^{\text{m}}$              |
|   `𝘃m`   |           $\bm{v}^{\text{m}}$            |
|  `∂𝘃mα`  |        $\bm{v}^{\text{m}}_{, α}$         |
| `∂∂𝘃mαβ` |       $\bm{v}^{\text{m}}_{, α β}$        |
|   `𝞂`    |      $\langle \bm{\sigma} \rangle$       |
|   `𝞂m`   | $\langle \bm{\sigma}^{\text{m}} \rangle$ |
|   `𝗠`    |         $\langle \bm{M} \rangle$         |
|   `𝗕a`   |             $[\mathbf{B}^a]$             |
|   `𝗕b`   |             $[\mathbf{B}^b]$             |
