```
phase_deg(c::Cut, ipol::Int)
phase_deg(c::Cut, polsymb::Symbol)
phase_deg(c::Cut, polstr::String = "copol")
```

カット内の特定の偏光の選択に対して、度単位の位相の行列を返します。`ipol`の合法的な値は1、2、または3です。`polstr`の合法的な値は「copol」（デフォルト）および「xpol」（大文字小文字は区別されません）です。`polsymb`の合法的な値は`:copol`および`:xpol`です。再度、大文字小文字は区別されません。返される値は、`length(get_theta(cut))`行と`length(get_phi(cut))`列を持つ`Matrix{Float64}`です。
