```
compute_angle_δᵥ(::TestRound, ::TrapQubit, θᵥ, rᵥ)
```

テストラウンドであり、キュービットがトラップキュービットである場合の角度 δᵥ を計算します。

δᵥ の計算ケース

2. ラウンド ≡ テスト ∩ キュービット ≡ トラップ  → δᵥ = θᵥ + rᵥπ

# 引数

  * `::TestRound`: テストラウンドを表す型。
  * `::TrapQubit`: トラップキュービットを表す型。
  * `θᵥ`: 角度 θᵥ。
  * `rᵥ`: 定数 rᵥ。

# 戻り値

計算された角度 δᵥ。

# 例

```julia
julia> compute_angle_δᵥ(TestRound(), TrapQubit(), 0, 0)
0
```
