````
PekerisUnderwaterEnv

Pekerisモデルにおける水中環境を表す型。

# フィールド
- `c1::T1`: 水柱内の音速。
- `cb::T1`: 底半空間内の音速。
- `ρ1::T1`: 水柱の密度。
- `ρb::T1`: 底半空間の密度。
- `depth::T1`: 水柱の深さ。

# コンストラクタ
```julia
PekerisUnderwaterEnv(c1::T1, cb, ρ1, ρb, depth) where {T1}
```

# 例
```julia
env = PekerisUnderwaterEnv(1500.0, 1600.0, 1000.0, 2000.0, 100.0)
```
````
