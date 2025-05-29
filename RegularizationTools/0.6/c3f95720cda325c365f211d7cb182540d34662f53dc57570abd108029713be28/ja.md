```
forwardmodel(
    s::AbstractVector{T1},
    x::AbstractVector{T2},
    f::Function,
)::AbstractArray where {T1<:Any,T2<:Number}
```

数値値 [x] をセットポイント [s] に対応させて出力 [y] を生成するフォワードモデルで、関数 f が与えられます。関数 f は [Domain](@ref) 型の単一引数を受け入れ、入力 $x$ とクエリポイント $q$ での出力 $y$ との間の数値マッピングを提供しなければなりません。

[designmatrix](@ref) とフォワードモデルは関連しています。

```
A = designmatrix(s, q, f)
y1 = A*x

y2 = forwardmodel(s, x, q, f)
y1 == y2
```
