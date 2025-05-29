```
issymplectic(basis::SymplecticBasis, x::T)
```

入力行列がシンプレクティック定義を満たすかどうかを確認します。

## 例

```jldoctest
julia> basis = QuadPairBasis(1);

julia> issymplectic(basis, [1.0 0.0; 0.0 1.0])
true
```
