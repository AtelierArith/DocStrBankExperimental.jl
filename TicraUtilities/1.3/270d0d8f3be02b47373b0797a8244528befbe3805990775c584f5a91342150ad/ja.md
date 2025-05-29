```
amplitude_db(c::Cut, ipol::Int)
amplitude_db(c::Cut, polsymb::Symbol = :copol)
amplitude_db(c::Cut, polstr::String = "copol")
```

カット内の特定の偏光の選択に対して、dBでの振幅の行列を返します。`ipol`の合法的な値は1、2、または3であり、3はカットに3つの偏光成分が存在する場合にのみ合法です。`polstr`の合法的な値は「copol」（デフォルト）と「xpol」です。大文字と小文字は区別されません。`polsymb`の合法的な値は`:copol`と`:xpol`です。再度、大文字と小文字は区別されません。Copolは、θ = ϕ = 0で最大振幅を持つ偏光として定義されます。
