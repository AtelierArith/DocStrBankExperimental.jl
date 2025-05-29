```
Bra(ψ :: Adjoint{T,Vector{T}}; atol=ATOL :: Float64) where T <: Number
```

複素値ヒルベルト空間の行ベクトル。ブラは随伴を介してケトに対する双対です。`Vector{<:Number}`型で呼び出されると、随伴は自動的に`ψ'`として取られます。

```julia
Bra(ψ :: Vector{<:Number}; atol=ATOL :: Float64)
```

同様に、`Ket`は随伴を介して`Bra`に変換できます。

```julia
Bra(ψ :: Ket; atol=ATOL :: Float64)
```

`Bra(ψ')`は、`ψ'`が正規化されていない場合に`DomainError`をスローします。
