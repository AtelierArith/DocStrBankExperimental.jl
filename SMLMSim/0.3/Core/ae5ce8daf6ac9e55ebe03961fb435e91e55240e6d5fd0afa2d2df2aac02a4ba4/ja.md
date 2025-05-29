```
kinetic_model(smld::BasicSMLD, f::Molecule, nframes::Int, framerate::Real;
             ndatasets::Int=1, minphotons=50.0, state1::Int=2)
```

既存の局所化データから運動的な点滅モデルを生成します。

# 引数

  * `smld::BasicSMLD`: 真のエミッタ位置を含む入力SMLD
  * `f::Molecule`: 運動的な速度を持つ蛍光体モデル
  * `nframes::Int`: シミュレーションするフレーム数
  * `framerate::Real`: フレームレート（Hz）
  * `ndatasets::Int=1`: 生成する独立したデータセットの数
  * `minphotons::Float64=50.0`: 検出のための最小光子数
  * `state1::Union{Int, Symbol}=:equilibrium`: 初期状態の指定:

      * `::Int`: 開始する特定の状態（1=オン、2=オフが一般的）
      * `:equilibrium`: 平衡分布からサンプリング（デフォルト）

# 戻り値

  * `BasicSMLD`: シミュレーションされた点滅運動を持つ新しいSMLD

# 詳細

入力SMLDの各ユニークな位置について:

1. 運動モデルを使用して蛍光体の点滅をシミュレートします
2. 光子数が閾値を超えるフレームのためにエミッタを作成します
3. 同じ位置からのエミッタをリンクするためにtrack_idを保持します
4. カメラを維持し、入力SMLDからメタデータを拡張します

# 例

```julia
camera = IdealCamera(1:128, 1:128, 0.1)
pattern = Nmer2D()
smld_true, _, _ = simulate(pattern=pattern, camera=camera)

# 点滅運動を追加
fluor = GenericFluor(; γ=10000.0, q=[-10.0 10.0; 1e-1 -1e-1])
smld_model = kinetic_model(smld_true, fluor, 1000, 10.0)
```

# 注意

エミッタのタイプ（2D/3D）は入力SMLDから自動的に決定されます。位置の不確実性は0に初期化され、apply_noise()関数を使用して設定できます。
