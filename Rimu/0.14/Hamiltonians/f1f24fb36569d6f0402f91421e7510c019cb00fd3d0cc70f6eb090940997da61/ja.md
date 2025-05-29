```
momentum(ham::AbstractHamiltonian)
```

Fock空間における線形演算子としての運動量。Fock基底に関する情報を伝えるためにハミルトニアン`ham`を渡します。運動量演算子を表す[`AbstractHamiltonian`](@ref)を返します。

注意: `momentum`は現在[`HubbardMom1D`](@ref)に対してのみ定義されています。

# 例

```jldoctest
julia> add = BoseFS((1, 0, 2, 1, 2, 1, 1, 3));


julia> ham = HubbardMom1D(add; u = 2.0, t = 1.0);


julia> mom = momentum(ham);


julia> diagonal_element(mom, add) # 単一の構成の運動量を計算
-1.5707963267948966

julia> v = DVec(add => 10; capacity=1000);


julia> rayleigh_quotient(mom, v) # 状態ベクトル`v`の運動量期待値
-1.5707963267948966
```

[`AbstractHamiltonian`](@ref)インターフェースの一部。
