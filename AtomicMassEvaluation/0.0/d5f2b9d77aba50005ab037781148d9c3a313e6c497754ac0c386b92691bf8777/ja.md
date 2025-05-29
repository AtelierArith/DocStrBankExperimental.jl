```
構造体 Isotope
    Z::Int
    N::Int
end
```

Isotope 構造体、コンストラクタは以下の通りです：

```julia
Isotope(iso::Isotope)
Isotope(Z::Integer, N::Integer)
Isotope(name::AbstractString) # 同位体の名前を解析します。例：`Ne20`
```
